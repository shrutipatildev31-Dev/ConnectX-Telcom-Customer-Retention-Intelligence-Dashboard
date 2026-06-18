###### **1. Which Age Group Has Highest Churn Risk?**



SELECT

&#x20;   age\_group,

&#x20;   tenure\_group,

&#x20;   ROUND(

&#x20;       100.0 \* SUM(CASE WHEN customer\_status='Churned' THEN 1 ELSE 0 END)

&#x20;       / COUNT(\*),2

&#x20;   ) AS churn\_rate

FROM telecom\_customer\_churn

GROUP BY age\_group, tenure\_group

ORDER BY churn\_rate DESC;



###### **2. What Are Top Churn Reasons?**



SELECT

&#x20;   churn\_reason,

&#x20;   COUNT(\*) AS churn\_count

FROM telecom\_customer\_churn

WHERE customer\_status='Churned'

GROUP BY churn\_reason

ORDER BY churn\_count DESC;

###### 

###### **3. Which Contract Type Has Highest Churn?**



SELECT

&#x20;   contract,

&#x20;   COUNT(\*) AS churned\_customers

FROM telecom\_customer\_churn

WHERE customer\_status='Churned'

GROUP BY contract

ORDER BY churned\_customers DESC;



###### **4. Which Internet Service Has Highest Churn?**



SELECT

&#x20;   internet\_type,

&#x20;   COUNT(\*) AS churn\_count

FROM telecom\_customer\_churn

WHERE customer\_status='Churned'

GROUP BY internet\_type

ORDER BY churn\_count DESC;



###### **5. Which Services Improve Retention?**



SELECT

&#x20;   online\_backup,

&#x20;   COUNT(\*) AS retained\_customers

FROM telecom\_customer\_churn

WHERE customer\_status='Stayed'

GROUP BY online\_backup;



SELECT

&#x20;   Online\_Security,

&#x20;   COUNT(\*) AS retained\_customers

FROM telecom\_customer\_churn

WHERE customer\_status='Stayed'

GROUP BY online\_backup;



SELECT

&#x20; Device\_Protection,

&#x20;   COUNT(\*) AS retained\_customers

FROM telecom\_customer\_churn

WHERE customer\_status='Stayed'

GROUP BY online\_backup;



SELECT

&#x20; Premium\_Tech\_Support,

&#x20;   COUNT(\*) AS retained\_customers

FROM telecom\_customer\_churn

WHERE customer\_status='Stayed'

GROUP BY online\_backup;





###### **6. Revenue Lost by Tenure Group**



SELECT

&#x20;   tenure\_group,

&#x20;   SUM(total\_revenue) AS revenue\_lost

FROM telecom\_customer\_churn

WHERE customer\_status='Churned'

GROUP BY tenure\_group

ORDER BY revenue\_lost DESC;

###### 

###### **7. Top Revenue Generating Cities**



SELECT TOP 10

&#x20;   zip\_code,

&#x20;   SUM(total\_revenue) AS revenue

FROM telecom\_customer\_churn

GROUP BY zip\_code

ORDER BY revenue DESC;



###### **8. Revenue by Payment Method**



SELECT

&#x20;   payment\_method,

&#x20;   SUM(total\_revenue) AS total\_revenue

FROM telecom\_customer\_churn

GROUP BY payment\_method

ORDER BY total\_revenue DESC;





