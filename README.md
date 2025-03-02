# Smart Logistics Analysis

## **Project Overview**

This project analyzes logistics delays to uncover root causes, identify trends, and provide actionable insights for improving supply chain efficiency. Using **SQL queries** and **Tableau visualizations**, the project focuses on:

- Identifying the most common delay reasons
- Examining the impact of traffic conditions on delays
- Tracking monthly delay trends to identify seasonal patterns

## **Business Problem & Key Performance Indicators (KPIs)**

**Problem:** Logistics delays impact operational efficiency, increase costs, and reduce customer satisfaction. The goal is to identify key bottlenecks and recommend data-driven solutions.

**KPIs:**

- **On-Time Delivery Rate** → Percentage of shipments arriving on time.
- **Delay Rate by Traffic Condition** → Impact of traffic on delivery performance.
- **Monthly Delay Trend** → Seasonal impact on supply chain operations.

---

## **1. Identifying Delay Causes**

### **SQL Query:**

```sql
SELECT Logistics_Delay_Reason, COUNT(*) AS Total_Count  
FROM smart_logistics_dataset  
WHERE Logistics_Delay = 1  
GROUP BY Logistics_Delay_Reason  
ORDER BY Total_Count DESC;
```

### **Findings & Business Impact:**
![delay](https://github.com/user-attachments/assets/71096642-0f34-4b84-95f5-e42a43c3907b)

- **Weather (151 delays)** → Unpredictable conditions cause disruptions; proactive planning is needed.
- **Mechanical Failures (133 delays)** → Equipment issues highlight the need for preventive maintenance.
- **"None" Category (147 delays)** → Indicates missing data, suggesting process inefficiencies.

### **Actionable Recommendations:**

- **Weather-Responsive Logistics Planning** → Integrate **real-time weather forecasts** and **dynamic rerouting**.
- **Preventive Maintenance Program** → Reduce mechanical failures through **scheduled inspections and IoT tracking**.
- **Data Integrity Improvements** → Enhance reporting accuracy to capture complete delay reasons.

---

## **2. Traffic Impact on Delays**

### **SQL Query:**

```sql
SELECT Traffic_Status, COUNT(*) AS Total_Shipments,  
       SUM(Logistics_Delay) AS Delayed_Shipments,  
       ROUND(100.0 * SUM(Logistics_Delay) / COUNT(*), 1) AS Delay_Percentage  
FROM smart_logistics_dataset  
GROUP BY Traffic_Status  
ORDER BY Delay_Percentage DESC;
```

### **Findings & Business Impact:**
![traffic](https://github.com/user-attachments/assets/cea2d26f-39de-498b-8838-93883fd99ee2)

- **Heavy Traffic (100% delay rate)** → Every shipment in high-traffic areas experiences delays.
- **Clear Traffic (35.1% delay rate)** → Delays still occur even when conditions are ideal, indicating internal inefficiencies.

### **Actionable Recommendations:**

- **AI-Powered Route Optimization** → Implement real-time traffic monitoring and dynamic route adjustments.
- **Operational Efficiency Review** → Investigate internal bottlenecks causing delays in clear traffic conditions.
- **Peak Traffic Scheduling** → Adjust delivery schedules to avoid congestion during known peak hours.

---

## **3. Monthly Delay Trends: Seasonal Impact**

### **SQL Query:**

```sql
SELECT SUBSTR(Timestamp, 1, 7) AS Month,  
       SUM(Logistics_Delay) AS Delayed_Shipments,  
       COUNT(*) AS Total_Shipments  
FROM smart_logistics_dataset  
GROUP BY Month  
ORDER BY Month;
```

### **Findings & Business Impact:**
![monthly](https://github.com/user-attachments/assets/c7f6285f-5669-453a-bb15-5bd0701cdc10)

- **March and July experience the highest delays**, suggesting seasonal demand surges.
- **Fluctuating delays across months** indicate inconsistent forecasting and resource planning.

### **Actionable Recommendations:**

- **Seasonal Capacity Planning** → Adjust staffing and fleet allocation during peak demand months.
- **Demand Forecasting Enhancement** → Utilize historical data to anticipate and mitigate seasonal disruptions.
- **Marketing-Logistics Coordination** → Align delivery schedules with sales promotions to prevent last-minute capacity overloads.



## **Documented Assumptions & Caveats**

- **Data Accuracy:** The dataset may contain missing or misclassified values, particularly in the "None" delay category.
- **Traffic Conditions:** Real-world application assumes dynamic rerouting is feasible within the logistics network.
- **Seasonal Trends:** Delay patterns may also be influenced by external economic or geopolitical factors.





## **Final Business Impact & Next Steps**

✅ **Operational Efficiency:** Addressing top delay causes can streamline logistics and reduce disruptions. 

✅ **Data-Driven Decision Making:** Enhanced forecasting enables better capacity planning. 

✅ **Scalability:** Recommendations can be expanded to new locations and supply chain networks.



