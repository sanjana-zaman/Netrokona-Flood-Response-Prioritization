[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.11](https://img.shields.io/badge/python-3.11-blue.svg)](https://www.python.org/)

> A geospatial decision support tool that translates gisbased data into union-level resource prioritization for disaster responders.

Built for **RIMES Marathon 2026** by Sanjana Zaman.

##  What This Tool Does

When flooding occurs in Netrokona District, Bangladesh, this tool answers 
one critical question for field coordinators:
**"Which unions need help first — and why?"**

It produces a ranked priority list of affected unions showing pre-computed vulnerability score, combining real time data and physical, infrastructural and historical vulnerability.

##  Study Area

**Netrokona District**, Mymensingh Division, Bangladesh  
Located in the haor belt — one of the most flood-prone regions in Asia.  
Bordered by Meghalaya, India to the north — source of catastrophic 
flash flood events including August 2024.


##  Methodology

### Vulnerability Index (Static — computed once pre-season)

Seven dimensions assessed at union level:
Population density, elevation, slope, drainage, previous flood extent, river proximity, rainfall intensity.


### Flood Impact Assessment (Dynamic — runs during flood event)

**Demo mode:** Uses August 2024 Netrokona flood extent  
**Live mode:** Connects to FFWC API — triggers when water levels  
exceed 90% of danger threshold at Durgapur/Bijoypur stations

##  Quick Start

### 1. Clone the repository
```bash
git clone https://github.com/sanjana-zaman/resilienceai-netrokona.git
cd resilienceai-netrokona
```

### 2. Create environment
```bash
conda env create -f environment.yml
conda activate resilienceai
```

### 3. Run the notebooks in order
```
notebooks/01_data_download.ipynb      → Download all data layers
notebooks/02_vulnerability_index.ipynb → Compute vulnerability scores, combine ffwc data


### 4. View outputs

outputs/static/netrokona_vulnerability_map.html  → Open in browser
outputs/live/priority_report_2024.csv           → Open in Excel


##  Repository Structure
```
resilienceai-netrokona/
├── config.yaml                    # Study area + parameter settings
├── environment.yml                # Reproducible Python environment
├── notebooks/
│   ├── 01_data_download.ipynb    # Data acquisition pipeline
│   ├── 02_vulnerability_index.ipynb  # PCA + UNESCO-IHE methodology
│ 
├── src/
│   ├── data_download.py          # Download functions
│   ├── preprocessing.py          # Normalization, reprojection
│   ├── vulnerability.py          # UNESCO-IHE formula + PCA
│   ├── flood_model.py            # Bathtub inundation model
│   ├── impact_assessment.py      # Population, facilities, roads
│   ├── priority_scorer.py        # Priority ranking
│   ├── ffwc_api.py               # Live FFWC API (operational mode)
│   └── dashboard.py              # Folium map generation
├── data/
│   ├── bundled/                  # Small reference files (committed)
│   └── processed/                # Pipeline outputs (gitignored)
└── outputs/
    ├── static/                   # Vulnerability maps
    └── live/                     # Flood event outputs
```

---

##  Data Sources

| Data | Source | License |
|---|---|---|
| Admin boundaries | GeoBoundaries | CC BY 4.0 |
| Population | WorldPop | CC BY 4.0 |
| Elevation (DEM) | NASA SRTM 30m | Public Domain |
| Roads & Infrastructure | OpenStreetMap | ODbL |
| Health facilities | HDX / LGED | CC BY |
| Flood shelters | GeoDASH Bangladesh | Open |
| Flood extent (2024) | Copernicus EMS | Free |
| Rainfall | NASA POWER | Public Domain |
| Land use | Esri Global LULC | CC BY 4.0 |


##  Operating Modes

### Demo Mode (this repository)
Uses the August 2024 Netrokona flood event.  
Runs fully offline after initial data download.  
Produces complete priority ranking output.

### Live Operational Mode (designed for RIMES/BWDB integration)
Connects to FFWC API (`ffwc.bwdb.gov.bd`)  
Polls water levels every 30 minutes  
Auto-triggers when stations reach 90% of danger level  
Designed for integration with RIMES FFWC DSS (launched July 2025)

---

##  Key References

- Sarker S. et al. (2025). Geospatial Approach to Assess Flash Flood 
  Vulnerability in a Coastal District of Bangladesh. *ISPRS IJGI*, 14, 194.
- Nirandjan S. et al. (2022). A spatially-explicit harmonized global 
  dataset of critical infrastructure. *Scientific Data*, 9, 150.
- RIMES (2025). FFWC Decision Support System Launch, Bangladesh.
- UNESCO-IHE Flood Vulnerability Index. http://www.unesco-ihe-fvi.org/

---

##  Competition

Built for **RIMES Marathon 2026**  
Category: Smart Geospatial Mapping & Disaster Impact Intelligence  
Focus: Bangladesh — Netrokona District Haor Region

---

## 📄 License




