# Exploratory Spatial Data Analysis (ESDA)

Replication code for ESDA tutorials published at [regio28.com](https://regio28.com). Each folder contains code for the same analysis implemented across different tools.

---

## 📂 Repository Structure

```
esda/
├── stata/       ← Stata do files
├── r/           ← R scripts (coming soon)
├── python/      ← Python notebooks (coming soon)
└── geoda/       ← GeoDa project files (coming soon)
```

---

## 📝 Tutorial Series

| # | Topic | Area | Blog Post | Code |
|---|---|---|---|---|
| 1 | ESDA: Poverty & Moran's I | Java Island | [regio28.com](https://regio28.com/2026/01/03/exploratory-spatial-data-analysis-stata-application-1/) | [stata/esda_pov_java_2024.do](stata/esda_pov_java_2024.do) |

---

## 🗺️ Case 1: Poverty in Java Island, 2024

**Blog post:** [Exploratory Spatial Data Analysis: STATA Application (1)](https://regio28.com/2026/01/03/exploratory-spatial-data-analysis-stata-application-1/)

### What this code does

| Step | Description |
|---|---|
| 1 | Load and convert shapefile (Java ADM2, 2016) |
| 2 | Merge shapefile with poverty data 2024 |
| 3 | Create choropleth poverty map |
| 4 | Build Thiessen polygon weights matrix (to handle archipelago) |
| 5 | Compute spatial weights (Queen contiguity + inverse distance) |
| 6 | Test global spatial autocorrelation: Moran's I & Geary's C |
| 7 | Run LISA & generate Moran scatterplot by quadrant |

### Key outputs

![Moran Scatterplot](https://i0.wp.com/regio28.com/wp-content/uploads/2026/01/adm2_java_oran_pov2024_quadrants.png?resize=800%2C582&ssl=1)

- **Moran's I = 0.159** → positive spatial autocorrelation (clustered pattern)
- High-High poverty clusters: Kebumen, Banyumas, Wonosobo, Purworejo
- Thiessen polygon used instead of Queen contiguity to handle island districts

### How to run

1. Open Stata
2. Run `esda_pov_java_2024.do` — all data downloads automatically from GitHub
3. Set your working directory at the top of the file

### Required Stata packages

```stata
ssc install genmsp, replace
ssc install shp2dta, replace
ssc install grmap, replace
```

### Data sources

All spatial and attribute data loads automatically via `copy` commands in the do file:

| File | Description | Source |
|---|---|---|
| `java_districts_2016.shp` | Java district boundaries | [rabdulah85/public](https://github.com/rabdulah85/public) |
| `java_districts_2016_tp.shp` | Thiessen polygon boundaries | [rabdulah85/public](https://github.com/rabdulah85/public) |
| `adm2_pov_java_2024.dta` | Poverty rate by district, 2024 | BPS via [rabdulah85/public](https://github.com/rabdulah85/public) |

---

## 📚 References

- Pisati, M. (2012). [Exploratory spatial data analysis using Stata](https://www.stata.com/meeting/germany12/abstracts/desug12_pisati.pdf). DESUG.
- Grekousis, G. (2020). [Spatial Analysis Methods and Practice](https://www.cambridge.org/core/books/spatial-analysis-methods-and-practice/4C135005A621335D06CC63EFF17E3913). Cambridge University Press.

---

## 👤 Author

**Rusli Abdulah** · PhD Student, GSID Nagoya University · INDEF Indonesia

[![Blog](https://img.shields.io/badge/Blog-regio28.com-0A66C2?style=flat&logo=wordpress&logoColor=white)](https://regio28.com)
[![GitHub](https://img.shields.io/badge/GitHub-rabdulah85-181717?style=flat&logo=github&logoColor=white)](https://github.com/rabdulah85)
