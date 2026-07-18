# Job Hunter

A tool to help find (and later, semi-automatically apply to) ideal job roles for friends.
First user: **Kingsley Cashion** — Austin, TX.

## Current status
- **Scope (confirmed):** find + track for now (no auto-apply yet).
- **Now a multi-friend tool** with three parts:
  - `admin/index.html` — **Admin HQ** (home base). Chat intake to add a friend → spins up a shareable Role Finder link (brief encoded in the URL `#p=` hash). Seeded with Kingsley + Carrie.
  - `finder/index.html` — **profile-driven Role Finder engine**. Defaults to **Carrie** (Austin tech-sales, AE + SDR/BDR, hybrid). Reads a `#p=<base64 brief>` to render any friend; auto-generates live-search cards from a brief when no verified roles exist yet.
  - `webapp/index.html` — **Kingsley's** bespoke Role Finder (household/family + organizing).

### People
- **Kingsley** — Austin; household & family + professional organizing. Bespoke page (`webapp/`).
- **Carrie** — Austin, **hybrid (≥2 days in-office, no full remote)**; tech/SaaS sales, mix of SDR/BDR → AE, Salesforce/SaaS baseline. Engine default (`finder/`). Verified-live employers 2026-07-18: Amazon Business (Hybrid AE $69–121k), Toshiba (Sr AE), AlertMedia, recruitAbility; Zello, LumenServe, ePayPolicy, LogicMonitor, TFLI, Vivax (SDR/BDR). Top source: **Built In Austin — Hybrid Sales**.

## Target profile — Kingsley
Two role directions, both in Austin:
1. **Household & Family** — nanny, family assistant, house manager, household manager, estate manager.
2. **Professional Organizing** — home/professional organizer at organizing studios.

## Verified-live employers (tested 2026-07-18)
Opened & confirmed as active Austin postings:
- **Household/Family:** The Nanny League ($35–40/hr), A Perfect Fit Nanny Agency ($32–37/hr), MOD Assistants ($24/hr), Sage Haus ($28–32/hr), That Nanny Place ($26–28/hr), Nanny & Butler (house manager).
- **Organizing:** The Cesta ($22–30/hr), Graceful Spaces (3 roles: Project Lead / Lead Organizer / Organizer).

## Link strategy (important finding)
Individual Indeed/LinkedIn job URLs **expire within days** — all 5 single-post LinkedIn links tested were already dead (404 or redirect to a generic listing). **Evergreen SEARCH URLs are what hold up** and always render current results. So the tool links to tested search URLs, not individual posts. Tested working search links live in `webapp` (`const L`).

## Sourcing map (where the roles live)
| Category | Best channels |
|---|---|
| Household & Family | Household-staffing **agencies** (Moms Best Friend, Seaside, Riveter, Mahler, BAHS) → **Indeed** → **LinkedIn** (mgr roles) → Care.com / Sittercity / Nanny Lane → local (Eanes ISD, FB groups) |
| Professional Organizing | **Direct company sites** (Graceful Spaces, Moxie Space, NEAT Method) → **Instagram** → ZipRecruiter/Indeed/SimplyHired → NAPO directory |

## Phased plan
- **Phase 0 – Search spec** — role titles, radius, comp floor, must-haves. ✅ drafted
- **Phase 1 – Sourcing map** — channels per category. ✅ (above / in webapp)
- **Phase 2 – Tracker** — SaaS webapp of candidate roles + fit tagging. ✅ `webapp/`
  - Verified-live postings, per-card **freshness tile**, **"why not a fit" popup** (captures Kingsley's reason), and a **Settings/training view** with editable include/exclude search notes + the tagged Right-fit / Not-for-me lists. All persisted in `localStorage`.
- **Phase 3 – Daily cadence (next)** — a scheduled run that: (1) re-queries the verified search URLs using the editable include/exclude prefs + the accumulated tag reasons as the prompt; (2) pulls fresh matches; (3) dedupes against what she's already seen; (4) surfaces new roles in the dashboard. The reason-popup + Settings training data built in Phase 2 is what feeds this. Still **find + review only — no auto-submit.**
- **Phase 4 – Assisted applier** — match + score + pre-draft applications; **human reviews & submits.**

## Guardrails (important)
- **No auto-submitting** applications and **no account creation** on Kingsley's behalf. Full auto-apply violates Indeed/LinkedIn ToS and risks account bans — the design is human-in-the-loop.
- The shared application credentials (`kingsleycashion.jobs@gmail.com` + password) are **not** stored in this repo. They stay with Kingsley for when she submits.

## Files
- `webapp/index.html` — self-contained candidate-roles dashboard (no build step; open in a browser or view the Artifact).
