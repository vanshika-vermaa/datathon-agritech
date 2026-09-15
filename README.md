# 🌾 Mandi-to-Market Supply Chain Optimizer

A data-driven AgriTech project developed for the **TransOrg AgentIQ Datathon – Track 3**.

The project combines mandi arrivals, market prices, MSP, weather, and transport data to analyse agricultural supply-chain conditions and identify mandis that may need attention.

## 🔗 Live Dashboard

**Live Project:** https://datathon-agritech.vercel.app/

---

## 📌 Problem

Agricultural supply chains involve many factors such as crop arrivals, market prices, MSP, weather conditions, and transportation.

When these datasets are analysed separately, it is difficult to understand where the major risks are.

Our project brings these datasets together and provides:

* Mandi and crop-level analysis
* Price vs MSP analysis
* Supply and arrival analysis
* Weather analysis
* Transport and warehouse analysis
* Mandi priority scoring
* An AI-powered data analysis agent

---

## 💡 What We Built

The project combines data preprocessing, supply-chain analysis, mandi risk scoring, recommendations, an AI data analysis agent, and an interactive dashboard.

The main components are:

### 1. Data Preparation & Supply Chain Analysis
We cleaned and combined the provided datasets to calculate useful indicators such as:

* Total crop arrivals
* Average modal price
* MSP gap
* Below-MSP price observations
* Transport delay rate
* Average transit time
* Rainfall and arrival patterns
* Mandi-level risk scores

### 2. AI Data Analysis Agent

The project includes an AI-powered data analysis agent that provides a natural-language interface to the project's agricultural supply-chain data.

The agent can understand analytical queries across the integrated datasets and generate the relevant results without requiring users to write code or database queries.

It supports:

- **Trend analysis** of arrivals, prices, and other time-based metrics
- **Crop-wise, mandi-wise, district-wise, and warehouse-wise comparisons**
- **Price and MSP analysis**, including wholesale price distributions
- **Supply analysis** using crop arrival quantities
- **Weather analysis** across different locations and time periods
- **Transport analysis** including transit time and delays
- **Warehouse-level analysis** of crop movement
- **Risk and priority analysis** using the calculated mandi risk scores

Depending on the query, the agent can return numerical results, comparisons, tables, or visualizations.

This makes the agent a natural-language data exploration layer over the supply-chain analysis rather than only a mandi information chatbot.

---

## 📊 Data Used

The project uses five main datasets provided for the challenge:

| Dataset             | Used For                                         |
| ------------------- | ------------------------------------------------ |
| Mandi Master        | Mandi, district, state and mandi information     |
| Mandi Arrivals      | Crop arrivals and quantities                     |
| Price & MSP         | Wholesale prices and MSP comparison              |
| Weather Sensors     | Temperature, rainfall and humidity               |
| Transport Logistics | Transit time, distance and warehouse information |

---

## 📖 Data Dictionary

The following tables describe the main fields used in the cleaned datasets.

### Mandi Master

| Column | Description |
|---|---|
| `Mandi_ID` | Unique identifier assigned to each mandi |
| `Mandi_Name` | Name of the mandi or grain market |
| `District` | District associated with the mandi |
| `State` | State associated with the mandi |
| `Mandi_Type` | Type of mandi, such as APMC, Private, or Direct |
| `Total_Area_Acres` | Total area of the mandi in acres |

### Mandi Arrivals

| Column | Description |
|---|---|
| `Arrival_ID` | Unique identifier for an arrival record |
| `Date` | Date of the crop arrival |
| `Mandi_ID` | Mandi where the crop arrived |
| `Crop_Name` | Original crop name from the dataset |
| `Variety` | Crop variety, when available |
| `Arrival_Quantity_Quintals` | Arrival quantity converted to Quintals |
| `Arrival_Quantity_Mt` | Arrival quantity in Metric Tonnes |
| `Arrival_Quantity_Kg` | Arrival quantity in Kilograms |
| `Reported_Quantity` | Quantity as originally reported |
| `Reported_Unit` | Original unit used for the reported quantity |
| `Farmer_Count` | Number of farmers associated with the arrival record |
| `Is_Arrival_ID_Imputed` | Indicates whether the arrival ID was filled during cleaning |
| `Is_Quantity_Negative_Flag` | Indicates whether the original quantity was negative |

### Price & MSP

| Column | Description |
|---|---|
| `record_id` | Unique identifier for the price record |
| `date` | Date of the price observation |
| `mandi_id` | Mandi associated with the price |
| `district` | District associated with the price record |
| `crop_name` | Crop name from the original dataset |
| `min_price` | Minimum recorded wholesale price |
| `max_price` | Maximum recorded wholesale price |
| `modal_price` | Modal wholesale price |
| `msp` | Minimum Support Price for the crop |

### Weather Sensors

| Column | Description |
|---|---|
| `sensor_id` | Identifier of the weather sensor |
| `timestamp` | Original sensor timestamp |
| `timestamp_tz` | Timezone associated with the original timestamp |
| `temperature_c` | Temperature converted to degrees Celsius |
| `rainfall_mm` | Rainfall converted to millimetres |
| `humidity_percent` | Relative humidity percentage |
| `is_sensor_unknown` | Indicates whether the sensor identity is unknown |
| `is_timestamp_missing` | Indicates whether the original timestamp was missing |
| `reported_temperature` | Temperature as originally reported |
| `reported_temperature_unit` | Original temperature unit |
| `reported_rainfall` | Rainfall as originally reported |
| `reported_rainfall_unit` | Original rainfall unit |
| `is_rainfall_negative_flag` | Indicates whether a negative rainfall value was present |

### Transport Logistics

| Column | Description |
|---|---|
| `Trip_ID` | Unique identifier for the transport trip |
| `Mandi_ID` | Mandi from which the trip originated |
| `Destination_Warehouse` | Warehouse receiving the shipment |
| `Departure_Time` | Recorded departure time |
| `Arrival_Time` | Recorded arrival time |
| `Transit_Hours` | Cleaned transit duration in hours |
| `Distance` | Recorded transport distance |
| `Distance_Unit` | Unit used for the recorded distance |
| `Vehicle_No` | Vehicle registration number |
| `Driver_ID` | Identifier of the driver |
| `Is_Arrival_Time_Imputed` | Indicates whether arrival time was imputed |
| `Is_Transit_Hours_Negative_Flag` | Indicates whether the original transit value was negative |
| `Is_Transit_Hours_Imputed` | Indicates whether transit hours were imputed |
| `Is_Driver_ID_Imputed` | Indicates whether the driver ID was imputed |


### Data cleaning included

* Standardizing mandi IDs
* Standardizing crop names
* Converting quantities into Quintals
* Cleaning price and currency values
* Standardizing dates
* Converting temperature to °C
* Converting rainfall to mm
* Converting UTC timestamps to IST
* Converting distances to kilometres
* Handling duplicates and missing values
* Cleaning vehicle registration formats
* Handling invalid/negative transport values

---

## 🔎 Key Results

Some of the main findings from the analysis:

* **25,000** mandi arrival records were analysed.
* The integrated price dataset contains **10,164** unique date-mandi-crop records after aggregation.
* **3,079** price observations were below MSP.
* **Wheat** had the highest crop-level price-crash rate at about **42.05%**.
* Average modal prices were above MSP for all six crops, although individual observations frequently fell below MSP.
* Daily rainfall and arrivals showed a correlation of only **0.022** in the aggregated analysis.
* **9,862** valid transport records were analysed.
* Using an analytical threshold of 18 hours, the overall transport delay rate was **26.57%**.

### Highest Priority Mandis

| Rank | Mandi                | Priority Score | Priority |
| ---: | -------------------- | -------------: | -------- |
|    1 | Orai Market          |          90.38 | Critical |
|    2 | Khandwa Grain Market |          89.09 | Critical |
|    3 | Dehri Mandi          |          89.00 | Critical |
|    4 | Gurgaon Grain Market |          87.93 | Critical |
|    5 | Guntakal Mandi       |          87.65 | Critical |

---

## ⚙️ Mandi Priority System

Each mandi receives three scores:

* **Price Risk Score**
* **Supply Pressure Score**
* **Transport Risk Score**

These are combined into a priority score:

```text
Priority Score =
50% Price Risk
+ 30% Supply Pressure
+ 20% Transport Risk
```

Mandis are then ranked as:

**Critical → High → Medium → Low**

The weights and the 18-hour transport delay threshold are analytical choices made for this project.

---

## 🛠️ Tech Stack

**Data Analysis**

* Python
* Pandas
* Jupyter Notebook

**Data Sources**

* CSV
* JSON
* Excel

**AI Agent & Application**

* Python
* JavaScript
* HTML
* Data-driven query processing

**Dashboard**

* Web-based dashboard
* Vercel

**Development**

* VS Code
* Git
* GitHub

---

## 🚀 Future Improvements

* Real-time mandi prices
* Live weather updates
* GPS-based transport tracking
* Crop price forecasting
* Route optimization
* Automated alerts for price crashes and delays
* More advanced natural-language data queries
* More detailed district-level and crop-level recommendations

---

## 👥 Team

Developed as part of the **TransOrg AgentIQ Datathon – Track 3: AgriTech**.

The project combines data cleaning, data analysis, supply-chain risk scoring, recommendations, an AI data-analysis agent, and an interactive web dashboard.

