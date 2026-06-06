
# USA Environmental Monitoring System

[![Earth Engine](https://img.shields.io/badge/Google-Earth%20Engine-4285F4)](https://earthengine.google.com/)
[![Python](https://img.shields.io/badge/Python-3.7+-3776AB)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

A comprehensive environmental monitoring dashboard for the contiguous United States (including Alaska and Hawaii) using Google Earth Engine. This tool analyzes land cover, temperature patterns, water resources, soil erosion risk, drought conditions, and urban heat islands.

## 📋 Features

| Layer | Description | Data Source |
|-------|-------------|-------------|
| **Land Cover** | NLCD 2021 Land Use/Land Cover | USGS NLCD |
| **Land Surface Temperature** | Annual/Seasonal LST patterns | MODIS MOD11A2 |
| **Water Bodies** | MNDWI-based water detection | Landsat 8 |
| **Soil Erosion** | RUSLE-based erosion risk index | SRTM + MODIS NDVI |
| **Drought Monitoring** | NDVI anomaly vs historical baseline | MODIS MOD13Q1 |
| **Vegetation Change** | NDVI change detection (2020-2024) | MODIS MOD13Q1 |
| **Topography** | Elevation, slope, hillshade | SRTM |
| **Urban Heat Island** | Urban vs rural temperature difference | MODIS + NLCD |

## 🗺️ Interactive Map Preview

The script generates an interactive Folium map with all layers clipped to the USA boundary:

- Toggle layers on/off
- Click for pixel values
- Export as PNG or GeoTIFF

## 🚀 Quick Start

### Prerequisites

```bash
# Install required packages
pip install earthengine-api geemap folium matplotlib numpy
```

### Authentication (First Time Only)

```python
import ee
ee.Authenticate()  # Opens browser for Google auth
ee.Initialize()
```

### Run the Script

```python
python usa_environmental_monitoring.py
```

## 📊 Outputs

### Interactive Map
- **File:** `gee_exports/USA_Environmental_Map.html`
- Open in any web browser

### Export to Google Drive (Optional)
Uncomment the export functions in the script:

```python
export_layer_to_drive(lst_mean, 'Mean_LST', 1000)
export_layer_to_drive(water_bodies, 'Water_Bodies', 30)
export_layer_to_drive(erosion_normalized, 'Erosion_Risk', 500)
```

### Thumbnail URLs
Quick preview images generated for:
- Land Surface Temperature
- NDVI Anomaly (Drought)
- Soil Erosion
- Water Bodies
- Elevation

## 📁 Project Structure

```
usa-environmental-monitoring/
├── usa_environmental_monitoring.py   # Main script
├── gee_exports/                      # Exported maps and data
│   └── USA_Environmental_Map.html    # Interactive map
├── requirements.txt                  # Dependencies
└── README.md                         # This file
```

## 🗺️ Layer Visualization Parameters

| Layer | Min | Max | Palette |
|-------|-----|-----|---------|
| LST | -20°C | 45°C | darkblue → darkred |
| NDVI Anomaly | -0.3 | 0.3 | darkred → darkgreen |
| Erosion Risk | 0 | 1 | green → darkred |
| Elevation | 0m | 3000m | green → white |
| UHI Intensity | -2°C | 4°C | blue → red |

## 📈 Analysis Period

- **Start Date:** 2020-01-01
- **End Date:** 2024-12-31
- **Historical Baseline:** 2015-2019 (for drought analysis)

## 🌎 USA Coverage

Includes all 50 states (CONUS + Alaska + Hawaii) using the LSIB 2017 boundary dataset.

**Total Area:** ~9.8 million km²

## ⚠️ Notes

- Processing time: 2-5 minutes depending on internet speed
- Some layers use 30m resolution (NLCD, Landsat)
- MODIS layers are 500m-1km resolution
- Exporting to Drive may take 10-30 minutes per layer

## 📄 License

MIT License - Free for academic and research use

## 🙏 Acknowledgments

- Google Earth Engine Team
- USGS for NLCD and Landsat data
- NASA for MODIS and SRTM data

## 📧 Contact

For issues or questions, please open a GitHub issue.

---

**Built with Google Earth Engine** 🌍
