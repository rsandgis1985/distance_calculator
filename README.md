═══════════════════════════════════════════════════════════
Site Distance Calculator - Help Document
═══════════════════════════════════════════════════════════

[Explanation of Calculation Method]

This program uses the Haversine formula to calculate the shortest distance between two points on the Earth's surface.

1. Formula principle
The Haversine formula takes into account the spherical characteristics of the Earth and calculates the arc length distance between two points on the sphere
   
a = sin²(Δlat/2) + cos(lat1) × cos(lat2) × sin²(Δlon/2)
c = 2 × arctan2(√a, √(1-a))
distance = R × c
   
among which
-Lat1, lon1: The latitude and longitude (in radians) of the first point
-Lat2, lon2: The latitude and longitude (in radians) of the second point
-R: The average radius of the Earth is 6371.0 kilometers
-C: The central angle (in radians) between two points

2. Accuracy analysis
Earth Model: Assuming the Earth is a perfect sphere with an average radius of 6371km
Global accuracy: ± 0.5% (actual Earth is an ellipsoid)
Short distance accuracy: For distances of 1-10 kilometers, the error is about ± 5-50 meters
Your data: The distance between stations is mainly 1-5 kilometers, with an estimated accuracy of ± 5-25 meters
   
Note: This accuracy is sufficient for most application scenarios. If centimeter level accuracy is required
For surveying and navigation, Vincent's formula or WGS-84 ellipsoid model can be used.

3. Scope of application
✓ Any two points worldwide
✓ Any distance (from a few meters to thousands of kilometers)
✓ Unrestricted by latitude
✗ Without considering altitude differences
✗ Without considering terrain obstacles

[Data format requirements]

The CSV file should contain three columns (in the same order):
Column 1: Site ID (such as PT1, NF1, QV1, etc.)
Column 2: Latitude (degrees, such as 35.4415)
Column 3: Longitude (degrees, such as 118.0406389)

example
ID,latitude,longitude
PT1,35.4415,118.0406389
PT2,35.44238889,118.0317222

Note:
The latitude and longitude are in decimal degrees format
North latitude is positive, South latitude is negative
East longitude is positive, West longitude is negative

[Function Description]

1. Load CSV file
Click the 'Load CSV File' button to select the data file, and the program will automatically attempt to load it
d: \ Users \ LYU \ Desktop \ Distance. csv

2. Calculate distance
Click the "Calculate Distance" button, and the program will:
Calculate the distance between all sites in pairs
Generate a complete distance matrix
• Automatically refresh all visual charts

3. Export distance matrix
Export the calculation results as a CSV file for easy viewing or further analysis in Excel

4. Data Preview (Tab 1)
Display the ID, latitude, and longitude information of all sites

5. Distance Matrix (Page 2)
• Complete distance matrix table (symmetric matrix)
• Statistical information: minimum/maximum/average/median distance

6. Map visualization (tab 3)
Red dots: Site location
• Blue thick line: Connection to stations located<5km away
Grey dashed line: Connection of stations with a distance of ≥ 5km
• Site tag: Display site ID

7. Distance statistics (tab 4)
• Top left: Distance distribution histogram
Top right: Bar chart of average distance for each site
• Bottom left: Distance heatmap (the darker the color, the farther the distance)
• Bottom right: Distance distribution boxplot

Your data analysis

According to the data you uploaded (around 35.4 ° N, 118.0 ° E):
• Location: Near Linyi City, Shandong Province, China
• Number of sites: 17 sites (PT1-6, NF1-6, QV1-5)
• Coverage: An area of approximately 3-4 kilometers by 3-4 kilometers
Expected distance between stations: 0.5-5 kilometers
• Calculation accuracy: ± 10-25 meters (already very accurate for this area)

【 Common Problems 】

Q: Why is the diagonal distance 0?
A: The diagonal is the distance from the site itself to itself, of course it is 0.

Q: Why is the distance matrix symmetric?
A: Because the distance from A to B=the distance from B to A.

Q: Is the calculation result accurate?
A: For your short distance application scenario (1-5 kilometers), the accuracy of Haversine formula
± 5-25 meters, fully meeting general requirements.

Q: How to verify the accuracy of calculations?
A: You can measure the distance comparison between two points on Baidu Maps/Amap, or use online
Verification of latitude and longitude distance calculator.

Q: Can we calculate the 3D distance considering altitude?
A: The current version only calculates horizontal distance. If you need 3D distance, you need to provide altitude data,
And use the Pythagorean theorem: d_3d=√ (d_2d ²+Δ h ²)

[Technical Parameters]

• Programming language: Python 3. x
Core libraries: pandas, numpy, matplotlib, tkinter
• Calculation method: Haversine formula
• Earth radius: 6371.0 km (recommended by IUGG)
• Output unit: kilometers (rounded to 3 decimal places)
• Angle unit: degrees (input) → radians (calculation)

═══════════════════════════════════════════════════════════
Version: 1.0 | Author: GitHub Copilot | Date: December 12, 2025
═══════════════════════════════════════════════════════════
