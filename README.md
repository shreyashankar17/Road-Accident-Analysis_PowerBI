
# Road Accident Analysis

Problem Statement and requirements-

Clients wants to create a Road Accident Dashboard for year 2021 and 2022 so that they can have insight on the below requirements-


1. Primary KPI - Total Casualties and Total Accident values for Current Year and YoY growth

2. Primary KPI's - Total Casualties by Accident Severity for Current Year and YoY growth

3. Secondary KPI's - Total Casualties with respect to vehicle type for Current Year

4. Monthly trend showing comparison of casualties for Current Year and Previous Year

5. Casualties by Road Type for Current year 155804

6. Current Year Casualties by Area/Location & by Day/Night

7. Total Casualties and Total Accidents by Location

Steps followed are-
1. Data Cleaning:

a. Corrected misspellings in the "Accident Severity" column:

Accessed Power Query Editor.
Identified rows containing "fetal" in the "Accident Severity" column.
Replaced "fetal" with the correct term "fatal" using the "Replace Values" function.

b. Created a Date table for time intelligence:

Generated a new Date table within Power BI using the "Calendar" function.
Ensured the table included relevant date fields (e.g., Year, Month, Day) for analysis.
 
2. Established relationships:

a. Created a many-to-one relationship:

Linked the Date table to the main accident data table.
Configured a many-to-one relationship between the Date table (one side) and the Date column in the accident data table (many side).
This relationship enables time-based analysis and calculations.
![image](https://github.com/shreyashankar17/Road-Accident-Analysis_PowerBI/assets/84956119/25a1db29-a147-49a4-b0b8-9c6488d330fb)

3. Primary KPIs:

Total Casualties and Total Accidents for Current Year and YoY Growth:

Measures created:

        CY Casualties = TOTALYTD(SUM(Data[Number_of_Casualties]), 'Calendar'[Date])

        CY Accident Count = TOTALYTD(COUNT(Data[Accident_Index]), 'Calendar'[Date])

        PY Casualties = CALCULATE(SUM(Data[Number_of_Casualties]), SAMEPERIODLASTYEAR('Calendar'[Date]))

        PY Accident Count = CALCULATE(COUNT(Data[Accident_Index]), SAMEPERIODLASTYEAR('Calendar'[Date]))

YoY Growth Calculation:

      Casualties YoY Growth = (CY Casualties - PY Casualties) / PY Casualties
      
      Accident Count YoY Growth = (CY Accident Count - PY Accident Count) / PY Accident Count 

4. Primary KPIs by Accident Severity:

Measures created (assuming a column named "Accident_Severity"): -      

      CY Fatal Casualties = TOTALYTD(SUM(Data[Number_of_Casualties]), 'Calendar'[Date]), Data[Accident_Severity] = "Fatal") 
      CY Serious Casualties = TOTALYTD(SUM(Data[Number_of_Casualties]), 'Calendar'[Date]), Data[Accident_Severity] = "Serious") 
      CY Slight Casualties = TOTALYTD(SUM(Data[Number_of_Casualties]), 'Calendar'[Date]), Data[Accident_Severity] = "Slight") 
 
YoY Growth Calculation (for each severity level):
Same formula as above, using the respective CY and PY measures for each severity.

![image](https://github.com/shreyashankar17/Road-Accident-Analysis_PowerBI/assets/84956119/8162a262-f390-4926-8c1b-d5c65f9708ff)

5. Within the vehicle type table, we consolidated vehicles into six distinct categories: agriculture, bike, bus, car, others, and van. We subsequently presented this categorized data within a multi-row card visualization alongside the current year's casualties for each for enhanced clarity and analysis.

![image](https://github.com/shreyashankar17/Road-Accident-Analysis_PowerBI/assets/84956119/8876a74f-a0c0-4eac-9e39-2d27f2463506)

6. An area chart displays the monthly trend of total casualties for both the current and previous years. The x-axis represents months, and the y-axis shows the sum of casualties. The legend utilizes the Year and Month hierarchy to differentiate data points, allowing for easy comparison and identification of trends.

![image](https://github.com/shreyashankar17/Road-Accident-Analysis_PowerBI/assets/84956119/a74920a4-ef65-4378-9cef-aee6618d51c0)

7. Current Year Casualties:


Area/Location: Urban/rural breakdown with CY casualties displayed in the legend.

Day/Night: Light condition comparison visualized in a donut chart, again linking casualties to each segment.

Road Type: Breakdown by road type using a bar chart, highlighting casualties alongside each category. Each bar represents the total number of casualties on a specific road type. 

![image](https://github.com/shreyashankar17/Road-Accident-Analysis_PowerBI/assets/84956119/f7e5f92a-e172-4a1a-bf1a-4f5af05f0fd6)                         
![image](https://github.com/shreyashankar17/Road-Accident-Analysis_PowerBI/assets/84956119/96d951db-4812-4774-b8ef-1923544621ce)

8. Total Casualties and Total Accidents by Location

 We used a map visualization to display the distribution of total casualties and total accidents by location. Each data point on the map corresponds to a specific location identified by the [field name] field in the local authority distribution table. Latitude and longitude coordinates were used for accurate placement. Color gradients [or other visual elements] represent the varying levels of [casualties/accidents] across different locations.

 ![image](https://github.com/shreyashankar17/Road-Accident-Analysis_PowerBI/assets/84956119/089a6862-17c1-41bf-badd-0f24c2a97879)
        
          Utilizing these methods, the final dashboard was assembled
![image](https://github.com/shreyashankar17/Road-Accident-Analysis_PowerBI/assets/84956119/b435ae2f-6e10-45c3-8ca8-55a9967f963b)

