# SignBridge

Two-way sign language app: sign to text and speech, speech or text to a signing avatar, plus a full Learn course.
The execution plan lives at `~/.claude/plans/ok-now-i-want-parsed-newell.md`. Follow it phase by phase.

## Layout
- `signbridge/`: Python package (config, landmarks, vocab, models, nlg, learn, server)
- `scripts/`: data download, extraction, training, evaluation, export
- `web/`: Jinja templates, static JS/CSS, reference sign animations, scroll-craft landing page
- `artifacts/` trained models and `reports/` metrics JSON: both committed
- `legacy/`: old code, parked. Nothing may import from it
- `docs/DECISIONS.md`: one line per deviation from the plan

## Rules
- Run everything from the repo root: `.venv/bin/python -m scripts.<name>` or `.venv/bin/python -m signbridge.server`
- Constants only in `signbridge/config.py`. The browser reads them from `GET /api/config`
- Feature math only in `signbridge/landmarks.py`, shared by training and live inference
- Never commit `data/` or `.env`. Never push
- No invented metrics: every number shown comes from `reports/*.json`
- Copy: no em dashes, no filler verbs (elevate, seamless, unleash, supercharge), no emoji icons
- Design: scroll-craft skill at `.claude/skills/scroll-craft/`; read `references/taste.md` before CSS or markup
- Smallest complete change (ponytail). Shortcuts get `# shortcut: <limit>, <when to upgrade>`

## Test
`.venv/bin/pytest -q`
