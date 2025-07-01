# Objective
To analyze and visualize the seasonal variation in vegetation over a region in Rajasthan, India, using NDVI (Normalized Difference Vegetation Index) data for the year 2021. The project focuses on tracking changes in vegetation cover before summer and after monsoon, providing insights into agricultural and ecological conditions.

# Dataset Used
Source: Google Earth Engine (GEE)

Dataset: NOAA/VIIRS/001/VNP13A1 – VIIRS NDVI 500m resolution, 16-day composite

Temporal Range: January 2021 to December 2021

Spatial Focus: A 20 km buffered area around Udaipur, Rajasthan (72.6144°E, 27.0238°N)

# Code Workflow
1. Initialization
Earth Engine authenticated using ee.Authenticate() and initialized with my GCP project.

2. AOI Definition
Defined an Area of Interest (AOI) as a circular buffer around a point in Rajasthan.
aoi = ee.Geometry.Point([72.6144, 27.0238]).buffer(20000)

3. Loading and Filtering NDVI Data
Loaded the VIIRS NDVI ImageCollection.
Filtered by date and AOI for 2021.

4. Extracting Time Series Data
Computed mean NDVI values for each image using .reduceRegion().

Converted to a DataFrame for plotting and saving.

Plotted a time series chart to visualize NDVI fluctuations over time.

5. Identifying Extremes
Extracted dates with the maximum and minimum NDVI in 2021.

6. Generating Visual NDVI Maps
Retrieved NDVI images for:

March (pre-summer, low vegetation)

September (post-monsoon, high vegetation)

Converted to NumPy arrays and visualized side-by-side using matplotlib.

7. Creating NDVI GIF
Loop from March to September.

Downloaded and visualized each NDVI image.

Generated a GIF showing temporal vegetation change using imageio.

# Results
A clear increase in NDVI was observed after the monsoon season.

Minimum NDVI: ~0.17 (March)

Maximum NDVI: ~0.55 (September)

NDVI Time Series plotted as .png

Side-by-side comparison map of March and September NDVI

GIF showing gradual greening of the region from March to September.

# Analysis & Insights
The project successfully captured the seasonal greening effect in semi-arid Rajasthan.

NDVI values increased significantly after monsoon rains, consistent with vegetation growth cycles.

This analysis helps monitor:

Agricultural health

Drought response

Vegetation dynamics over time

No training or machine learning was used, as NDVI is computed directly from the satellite data bands using a standard formula:

NDVI
=
NIR-RED/
NIR+RED
​
![image](https://github.com/user-attachments/assets/0c0f0d2c-8bbb-46f6-b4ed-6e6e17f9d550)

![image](https://github.com/user-attachments/assets/e7eaf7c8-696c-458f-9192-ed7e10a08872)

![image](https://github.com/user-attachments/assets/08b7e96d-7f6d-4ea8-a872-7f21aad7d3e2)


### CLICK ON THIS GIF BELOW TO VISUALLY SEE VEGETATION INDEX CHANGE FROM SUMMER TO MONSOON 👇
![ndvi_timelapse_mar_to_sep](https://github.com/user-attachments/assets/32d21272-3daa-4d00-bee8-8164ef580602)

# Possible Extensions
Compare multiple years (e.g., 2020 vs. 2021)

Add rainfall data overlay for correlation

Use higher-resolution Sentinel-2 NDVI for finer details

Build a web-based dashboard to interactively explore NDVI changes

