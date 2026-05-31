# Australia by Road

A data visualisation exploring when to drive Australia's five iconic road trips.

**Live site:** https://virgohil16.github.io/australia-by-road/

## Thesis

*When* you drive matters more than *where* you drive. Using a derived "drive score"
that combines Bureau of Meteorology temperature and rainfall data, this visualisation
reveals which Australian routes are forgiving year-round and which have a narrow
weather window. Some routes — the Stuart Highway, the Nullarbor — accept travellers
almost any month. The Gibb River Road has just six.

## Five routes covered

1. **Great Ocean Road** (VIC) — 243 km, Torquay → Allansford
2. **Gibb River Road** (WA) — 660 km, Derby → Kununurra
3. **Pacific Highway** (NSW/QLD) — 790 km, Sydney → Brisbane
4. **Nullarbor Crossing** (WA/SA) — 1,200 km, Norseman → Ceduna
5. **Stuart Highway** (NT/SA) — 2,720 km, Darwin → Port Augusta

## Methodology

The drive score is a custom metric combining temperature and rainfall, calibrated for
a comfort-focused holidaymaker rather than a hardened outback traveller:

- Months above 33 °C → heat penalty (scales with excess, capped at 50)
- Months below 18 °C → cold penalty (capped at 40)
- Months above 75 mm of rain → wet penalty (capped at 50)
- Months above 40 mm of rain → minor showery penalty (capped at 15)
- Score = 100 minus total penalties; bounded at 0–100

Rating bands: Ideal ≥ 72 · OK ≥ 48 · Avoid < 48.

## Data sources

- **Climate:** Bureau of Meteorology long-term monthly averages, sampled at one
  representative town per route (Derby, Alice Springs, Coffs Harbour, Apollo Bay, Nullarbor)
- **Tourism:** Tourism Research Australia (TRA), 2023–24 domestic data
- **Route distances:** Visit Victoria, Tourism WA, Main Roads NT, Wikipedia
- **Map geometry:** [rowanhogan/australian-states](https://github.com/rowanhogan/australian-states)

## Technology

- HTML + CSS
- [Vega-Lite v5](https://vega.github.io/vega-lite/) for all ten visualisations
- Google Fonts: Fraunces (display) + Inter (body)
- No build step. JSON specifications in `vega/` are directly readable.

## Project structure

```
.
├── index.html              # Main page with all 10 charts
├── css/style.css           # Typography, layout, colour
├── vega/                   # 10 Vega-Lite chart specs
├── data/                   # Source data (JSON)
└── README.md               # This file
```

## Visualisations

1. **Choropleth** — Tourism spend by state (context)
2. **Hero map** — Five iconic routes drawn on Australia
3. **Route stat cards** — Distance, days, endpoints (small multiples)
4. **Km per ideal month** — Derived metric: distance ÷ ideal driving months (lollipop)
5. **Seasonality heatmap** — Drive score by month per route (the thesis chart)
6. **Climate small multiples** — Monthly temperature lines per route, points by rating
7. **Rainfall heatmap** — Monthly rainfall per route
8. **Latitude span** — Range bars showing geographic spread per route
9. **Connected scatterplot** — Each route's annual climate journey as a loop
10. **Radial year** — A year on the Gibb River Road as a clock face

## AI acknowledgement

As permitted by the assignment brief, Claude (Anthropic) was used to assist with
Vega-Lite syntax, CSS layout, prose editing, and data-pipeline troubleshooting.
All design decisions — the thesis, the drive-score formula and thresholds,
the chart choices, the story flow — were made by the author.

## Author

Vir Gohil · Student ID 35608900 · FIT2179 Data Visualisation 2 · Monash University · 2026
