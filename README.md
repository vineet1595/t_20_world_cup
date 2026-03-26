# 🏏 T20 World Cup 2022 — Best XI Cricket Team Selection Using Data Analytics

![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Python](https://img.shields.io/badge/Python-Pandas-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Web Scraping](https://img.shields.io/badge/Web%20Scraping-Bright%20Data-FF6B35?style=for-the-badge)
![Data Analytics](https://img.shields.io/badge/Data-Analytics-0078D4?style=for-the-badge)

---

## 📌 Problem Statement

Cricket is as much a game of strategy as it is of skill. With thousands of player performances available as data, how do we **objectively identify the best 11 players** in the world for a high-stakes T20 match?

This project tackles a hypothetical but analytically rigorous challenge:

> **"If Earth had to field its best-ever T20 XI, which 11 players from the T20 World Cup 2022 would you pick — and can you back it up with data?"**

### 🎯 Team Goals
The selected team must be capable of:
- **Scoring 180+ runs on average** when batting
- **Defending 150+ runs** when bowling
- Maintaining a **safety margin of at least 30 runs**

### 🧩 The Challenge
Selecting such a team requires answering several complex questions:
- Which openers have the best combination of strike rate and boundary percentage?
- Who are the most reliable middle-order anchors under pressure?
- Which fast bowlers and spinners are the most economical wicket-takers?
- How do we balance batting firepower with bowling variety?

Answering these questions purely on intuition leads to bias. This project answers them **with data**.

---

## 🗂️ Project Overview

| Attribute | Details |
|---|---|
| **Data Source** | ESPNcricinfo — T20 World Cup 2022 |
| **Scraping Tool** | Bright Data (JavaScript Collectors) |
| **Data Processing** | Python (Pandas) |
| **Visualization** | Microsoft Power BI |
| **Final Output** | Interactive dashboard + Best XI selection |

---

## 🔄 Project Workflow

```
Web Scraping (ESPNcricinfo)
        ↓
JSON Data Storage
        ↓
Python Pandas — Cleaning & Transformation
        ↓
CSV Export
        ↓
Power BI — Data Modeling & DAX
        ↓
Interactive Dashboard
        ↓
Final Best XI Selection
```

---

## 📊 Data Collected

Four datasets were scraped from ESPNcricinfo:

1. **Match Results Summary** — Match outcomes, teams, dates, venues
2. **Batting Scorecards** — Runs, balls, fours, sixes, strike rate, dismissal info
3. **Bowling Scorecards** — Overs, runs conceded, wickets, economy, dot balls
4. **Player Information** — Player profiles, teams, batting/bowling styles

---

## 🧹 Data Cleaning & Transformation (Python Pandas)

Key steps performed:

- Flattened nested JSON arrays into tabular DataFrames
- Converted dismissal information into binary `out` / `not out` columns
- Cleaned player names by removing special characters and captain markers `(C)`
- Created **unique Match IDs** by linking team names across datasets using a dictionary approach that handles team order variations
- Exported clean DataFrames to CSV for Power BI import

---

## 🔧 Data Modeling in Power BI

- Imported CSVs and transformed data using **Power Query**
- Created a **Star Schema** with:
  - Fact Tables: Batting, Bowling, Match Summary
  - Dimension Table: Players
- Linked tables via `match_id` and player name keys
- Created **DAX Measures** for:
  - Total runs, innings batted, innings dismissed
  - Batting average, strike rate, boundary %
  - Bowling economy, bowling strike rate, wickets taken, dot ball %
- Organized measures into folders (Batting / Bowling) for clarity

---

## 📋 Player Role Selection Criteria

| Role | Key Metrics |
|---|---|
| **Openers (Power Hitters)** | Avg > 30, Strike Rate > 140, Boundary % > 50%, Position ≤ 4 |
| **Middle Order Anchors** | Higher avg, consistent balls faced, variable strike rate |
| **Finisher** | High strike rate, innings stabilizer, batting-focused |
| **All-Rounders** | Bat Avg > 15, SR > 140, Bowl Eco < 7, Bowl SR < 20 |
| **Spinners** | Bat Avg > 15, SR > 140, Bowl Eco < 7, Bowl SR < 20 |
| **Fast Bowlers** | Economy < 7, SR < 16 balls/wicket, Dot Ball % > 40%, Innings > 4 |

---

## 📈 Dashboard Features

- **Player comparison tables** with dynamic filtering by role and performance thresholds
- **Scatter plots** — Strike Rate vs Batting Average, Economy vs Wickets
- **Bar charts** — Runs scored, wickets taken by player
- **Criteria sliders** — Dynamically filter players meeting specific stat thresholds
- **Tabs** for each player role: Power Hitters, Anchors, Finishers, All-Rounders, Bowlers

---

## 🏆 Final Best XI Selection

### Batting
| Player | Role | Key Stat |
|---|---|---|
| Jos Buttler *(WK)* | Opener | High boundary %, consistent avg |
| Rilee Rossouw | Opener | Explosive strike rate |
| Virat Kohli | Middle Order Anchor | Highest avg in tournament |
| Suryakumar Yadav | Middle Order | 360° striker, elite SR |
| Glenn Phillips | Middle Order | Reliable under pressure |

### All-Rounders
| Player | Role | Key Stat |
|---|---|---|
| Marcus Stoinis | All-Rounder | Bat SR + bowling economy |
| Shadab Khan | Spin All-Rounder | Wicket-taking + batting |
| Sikandar Raza | Spin All-Rounder | Economy + consistency |
| Glenn Maxwell | All-Rounder | Explosive bat + off-spin |

### Bowling
| Player | Role | Key Stat |
|---|---|---|
| Sam Curran | Fast Bowler | Best bowling economy |
| Anrich Nortje | Fast Bowler | Highest dot ball % |
| Shaheen Shah Afridi | Fast Bowler | Early wicket-taker |

> **Reserve:** Alex Hales (Opener)  
> ❌ **Notable Exclusion:** Mitchell Starc — did not meet bowling economy and strike rate thresholds

### Team Performance Summary
| Metric | Target | Achieved |
|---|---|---|
| Avg runs per player | ~37–39 | ✅ |
| Team strike rate | > 150 | ✅ |
| Bowling economy | < 7 | ✅ |
| Wicket-taking frequency | Disrupts top order early | ✅ |

---

## 💡 Key Learnings

- **Web scraping at scale** requires proxy rotation (Bright Data) to avoid IP blocking
- **Data linking** across multiple datasets needs careful design of unique keys (match IDs)
- **Power BI star schema** enables fast, flexible querying across large cricket datasets
- **DAX measures** provide dynamic, context-aware calculations for player comparisons
- **Data-driven selection** removes bias and surfaces non-obvious player choices
- Dashboard **design and aesthetics** are critical for stakeholder engagement and decision-making

---

## 🛠️ Tech Stack

```
├── Web Scraping     → Bright Data (JavaScript Collectors)
├── Data Storage     → JSON → CSV
├── Data Processing  → Python 3.x, Pandas
├── Visualization    → Microsoft Power BI Desktop
└── Data Modeling    → Power Query, DAX, Star Schema
```

---

## 📁 Repository Structure

```
t20-cricket-analytics/
│
├── data/
│   ├── raw/                  # Scraped JSON files
│   └── processed/            # Cleaned CSV files
│
├── notebooks/
│   └── data_transformation.ipynb   # Pandas cleaning & transformation
│
├── power_bi/
│   └── cricket_dashboard.pbix      # Power BI dashboard file
│
├── scraping/
│   └── bright_data_collectors/     # JS scraping scripts
│
└── README.md
```

---

## 🚀 How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/t20-cricket-analytics.git
   cd t20-cricket-analytics
   ```

2. **Install Python dependencies**
   ```bash
   pip install pandas jupyter
   ```

3. **Run the data transformation notebook**
   ```bash
   jupyter notebook notebooks/data_transformation.ipynb
   ```

4. **Open Power BI dashboard**
   - Open `power_bi/cricket_dashboard.pbix` in Power BI Desktop
   - Refresh the data source to point to your local CSV files

---

## 🙌 Acknowledgements

- **Data Source:** [ESPNcricinfo](https://www.espncricinfo.com/)
- **Scraping Infrastructure:** [Bright Data](https://brightdata.com/)

---

## 📬 Connect

If you found this project interesting, feel free to connect or raise an issue!

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)]((https://linkedin.com/in)/vm62)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github)](https://github.com/vineet1595)
