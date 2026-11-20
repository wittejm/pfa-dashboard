# Where Preschool for All Dollars Go

A static page showing every budgeted dollar of Multnomah County's Preschool for All Program Fund, by line item, for fiscal years 2026 and 2027.

## Run it

```
python3 -m http.server 8765
```

Then open http://localhost:8765. The page fetches the CSVs in `data/`, so it needs a web server; opening `index.html` from the filesystem shows an error message.

## Layout

- `index.html` is the whole page: markup, styles and script, no build step.
- `data/offers.csv` has one row per county program offer, with FY2026 and FY2027 adopted amounts.
- `data/fund.csv` has fund totals, reserves and dedicated savings (offers 25200A, 25200B, 25200C).
- `data/balance.csv` has year-end fund balances, each with its source.
- `data/fy24_actuals.csv` has actual FY2024 spending by category from the County Auditor's April 2025 report.
- `data/seats.csv` has seat and location counts from the performance measures in offer 25205A.
- `sources/` holds the county's program offer PDFs the figures were transcribed from.

## Updating for a new budget year

Program offers are at `https://multco.us/file/<offer>-<yy>_adopted.pdf/download`, listed at `https://multco.us/info/fy-20<yy>-program-offers`. Offer numbers change between years (25203 became 25203A and 25203B in FY2027), so check the listing. The page computes planned spending as fund total minus reserves minus dedicated savings and shows any difference from the itemized offers as "Not itemized"; a remainder near zero means every offer has been found.

## Known gap

FY2027 itemized offers total $280,191,484 against planned spending of $280,850,789. The $659,305 difference is shown as "Not itemized". The FY2026 offers for the Chair's Office (10000A), expanded communications (10007B) and the Health Department mental health team (40099B) have no FY2027 document under the same number.
