# Changelog

All notable changes to this project are documented in this file.

## v0.2.0 - 2026-03-12

### Added
- Added new Telegram command format:
  - `/s <bank_code> <account_number> <total_amount> <num_people> [note]`
- Added bank alias mapping service from text file.
- Added `data/bank_bins.txt` with mappings:
  - `ocb=970448`
  - `vcb=970436`
  - `bidv=970418`
  - `tpbank=970423`

### Changed
- Kept legacy `/s <total_amount> [num_people] [note]` command and made parser support both formats.
- Updated webhook flow to use dynamic bank/account from command when provided.
- Updated dashboard root page command help.
- Updated README command usage and bank mapping docs.
- Improved env parsing so placeholder/empty `TELEGRAM_WEBHOOK_SECRET` does not force webhook secret validation in development.

### Removed / Cleanup
- Removed old build artifact folder `dist/`.
- Removed old database dump `db/expenses.sql` and empty `db/` directory.
- Cleaned `.env` by removing unused legacy keys (`DATABASE_URL`, `DIRECT_URL`, `SERVER_SECRET`, `PAY_TOKEN_TTL_SECONDS`, `ADMIN_DASHBOARD_KEY`).

## v0.1.0

### Initial baseline
- Minimal TypeScript Express backend for Telegram webhook.
- Supported `/s <total_amount> [num_people] [note]`.
- Generated and sent VietQR split-payment QR to Telegram group.
- Basic health endpoint and root dashboard page.
- Vercel serverless entrypoint via `api/index.ts`.
