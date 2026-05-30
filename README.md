# Oil vs S&P 500 Event Analyzer

> Geopolitical Shocks & Market Impact Analysis — Python Programming Project  
> **Nidhi Tangam Dayananda** | Bloomberg Terminal & Yahoo Finance

[![GitHub Pages](https://img.shields.io/badge/Live%20Site-GitHub%20Pages-00ffaa?style=flat-square)](https://YOUR_USERNAME.github.io/oil-spx-analyzer)

---

## Overview

This project analyses the dynamic relationship between crude oil prices and the S&P 500 equity index across **2,828 trading days** (December 2014 – March 2026). Using a modular Python package built from scratch, the analysis examines **eight major geopolitical and macroeconomic event windows** and extends to **26 individual S&P 500 stocks** across six sectors.

**Central finding:** Oil and the S&P 500 are weakly correlated on average (β = 0.091, R² = 0.054), but geopolitical supply shocks fundamentally reverse this relationship. During the 2025–2026 US-Israel-Iran War, oil rose +41.4% while the S&P 500 fell −5.2%, producing a correlation of −0.50.

---

## Repository Structure

```
oil-spx-analyzer/
├── index.html                  # GitHub Pages dashboard site
├── README.md
├── Oil_vs_SP500_-_Impact___Analysis.ipynb   # Full analysis notebook
├── Oil_vs_S_P500_Analyzer.pdf              # Project report PDF
└── oil_spx_analyzer/           # Python package (if sharing source)
    ├── data_loader.py
    ├── analyzer.py
    ├── events.py
    ├── report.py
    └── multi_stock.py
```

---

## Key Results

| Metric | Value |
|--------|-------|
| Full-sample R² | 0.054 |
| OLS Beta (β) | 0.091 |
| Oil Annualised Volatility | 45.70% |
| SPX Annualised Volatility | 17.86% |
| Oil shock frequency (>3%) | 17.4% of all trading days |
| Peak negative correlation (Jun 2025) | −0.92 |
| Iran War 2026 correlation | −0.50 |

### Event Windows

| Event | Period | Oil Return | SPX Return | Correlation |
|-------|--------|-----------|-----------|-------------|
| Iran: Soleimani Killing | Jan 2020 | −16.9% | −0.2% | +0.11 |
| COVID-19 Crash | Feb–Apr 2020 | −41.5% | −9.97% | +0.27 |
| Oil Price War | Mar–Apr 2020 | −79.0% | −17.9% | +0.43 |
| Post-COVID Recovery | May–Dec 2020 | +94.6% | +25.4% | +0.38 |
| Russia–Ukraine War | Feb–Apr 2022 | +17.2% | −8.9% | −0.18 |
| Iran: Israel Strikes | Jun 2025 | −4.7% | +0.8% | **−0.92** |
| Iran: Full US-Israel War | Feb–Mar 2026 | **+41.4%** | −5.2% | −0.50 |
| Iran: Hormuz Closure | Mar–Apr 2026 | +41.4% | −5.2% | −0.50 |

---

## Methodology

- **Log returns:** `r(t) = ln(P(t) / P(t−1))` for stationarity
- **Rolling correlation:** 30-day Pearson, to capture regime shifts
- **OLS regression (Part A):** `SPX(t) = α + β × Oil(t) + ε(t)` via NumPy normal equations
- **Multiple regression (Part B):** `Stock(t) = α + β₁·Oil(t) + β₂·SPX(t) + β₃·VIX(t) + ε(t)` — isolates pure oil sensitivity controlling for broad market and volatility
- **Shock detection:** |oil return| > 3% ≈ 2σ threshold

No external statistical packages (statsmodels, seaborn) — only `pandas`, `numpy`, `matplotlib`, and `yfinance`.

---

## Deploying to GitHub Pages

1. Create a new GitHub repository
2. Upload all files (including `index.html`) to the root
3. Go to **Settings → Pages → Source → Deploy from branch → `main` / `root`**
4. Your site will be live at `https://YOUR_USERNAME.github.io/REPO_NAME`

---

## Data Sources

- **Bloomberg Terminal** — SPX daily closing prices, CL1 crude oil front-month futures (Dec 2014–Mar 2026)
- **Yahoo Finance / yfinance** — 26 S&P 500 stocks, VIX Volatility Index (Part B)

---

*Python Programming Project | Bloomberg Terminal & Yahoo Finance*
