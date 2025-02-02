# Data-Cleaning-in-Python

A: QUESTION:

What factors influence churn rate?


C1: PLAN TO ASSESS QUALITY OF DATA:


To find missing values: I downloaded numpy pandas and used isna() and isnull() function to see if there are any missing values in the data. 
To find duplicate values: I used the duplicated() function to see if there are any values that are duplicated.
To detect outliers: I plotted histograms for all the variables to check and see which one had outliers, then I plotted the ones with outliers in boxplots and used the median to impute the outliers to have a normal distribution.

C2: JUSTIFICATION OF APPROACH:

I used isna and isnull to find missing values because it the easiest and most common way to find null values and can be done quickly.
I used the duplicated() function to be able to find duplicated data because it is the way I learned how to find duplicates in python.
I used a histogram to find outliers because it is the most visual way to see outliers and are easily detected by looking for bars that look unusual from the normal distribution.

C3: JUSTIFICATION OF TOOLS:

I used python to clean my data because I would like to grow my skills in python, also because it is used more in the data science world as compared to R since there are a lot more packages and different ways to integrate it with other tools in a company. 

I used the following tools in Python: 
Pandas, math, numpy, matplotlib.pyplot, scipy.stats, sklearn.decomposition
I used Pandas to read the CSV, and read the DataFrame information.
I used numpy to find missing values using isna() and also look for duplicate rows using duplicate().
I used matlotlib.pyplot to plot graphs and create visualizations.
I used SciPy to create boxplots and detect normalization of each graph.
I used sklearn in order to run a PCA.


D1: CLEANING FINDINGS:

Duplicates: I did not find any duplicated in the data.

Missing data: For the missing values there were 8 columns that had missing values.
-	Children had 2495 missing values
-	Age had 2475 missing values
-	Income had 2490 missing values
-	Techie had 2477 missing values
-	Phone had 1026 missing values
-	TechSupport had 991 missing values
-	Tenure had 931 missing values
-	Bandwidth_GB_Year had 1021 missing values
 
Outliers: The columns that have outliers are: Income, Outage_sec_perweek, Email, Contacts, Yearly_equip_failure, and MonthlyCharge.


-	Income contained 709 number of outliers and the range of those outliers are from $65,000 to $300,000
 ![image](https://github.com/user-attachments/assets/964016ef-0e4e-429c-bc49-9fd27d98f10c)


-	Outage_sec_perweek contained 503 number of outliers and the range of those outliers are from 2.5 seconds and blow and an upper limit of 17 seconds to 60 seconds
  ![image](https://github.com/user-attachments/assets/a518be00-ea5d-441d-838b-52fdcc17c456)


-	Email contained 15 number of outliers and the range of those outliers are from 4 and below and an upper limit of 20 and above
![image](https://github.com/user-attachments/assets/10197701-8eea-439b-b9ea-2c83b87a2afc)


-	Contacts contained 8 number of outliers and the range of those outliers are from 5 to 7
![image](https://github.com/user-attachments/assets/0acfee36-cc9c-4d40-bde5-57d4a1ed5759)


-	Yearly_equip_failure contained 94 number of outliers and the range of those outliers are from 2 to 6
 ![image](https://github.com/user-attachments/assets/def56c50-b3d9-4e47-9e03-8be870c2dd89)


-	MonthlyCharge contained 3 number of outliers and the range of those outliers are from 300 and above
![image](https://github.com/user-attachments/assets/a04a9110-0793-4104-9f9b-82ca2402e6d2)

 

D2: JUSTIFICATION OF MITIGATION METHODS:

I did not find duplicates in the data but if I did, I would drop the duplicated rows.

For the missing values, I used the mean if the data was normally distributed, the median when the data is skewed or bi-modal and used the mode when it was a categorical data. 

-	'Children' I filled the NAs with the median because it is positively skewed
-	'Age' I filled the NAs with the mean because it has a normal distribution
-	'Income' I filled the NAs with the mean because it has a normal distribution
-	'Techie' I filled the NAs with the mode because it is categorical data 
-	'Phone' I filled the NAs with the mode because it is categorical data
-	'TechSupport' I filled the NAs with the mode because it is categorical data 
-	'Tenure' I filled the NAs with the mode because it is categorical data
-	‘Bandwidth_GB_Year' I filled the NAs with the mode because it is categorical data
  
For outliers I first used a boxplot to plot all the categorical values and see if they had outliers. Then for the ones that did have outliers I decided to impute them using the median for all the variables. 
The variables that I treated where: Income, Outage_sec_perweek, Email, Contacts, Yearly_equip_failure, and MonthlyCharge.

I first plotted them using boxplots, then I ran a query to see how many outliers there were, then I turned the outliers into NAs, then I replaced the NAs with the median so that all the outliers are now normal values. I used the median for each variable because the mean can highly influence the outliers and median are less sensitive to outliers.


D3: SUMMARY OF THE OUTCOMES:            

I checked for duplicates and found none, so the dataset has no redundant entries. For missing data, I used different methods based on the data distribution: the mean for normally distributed data, the median for skewed data, and the mode for categorical data. I made these choices after looking at histograms to ensure the data looked right. Now, there are no missing values. I handled outliers by identifying them with boxplots and then replacing them with the median to keep the data balanced without extreme values. Now, all variables are even, with no missing values or outliers.

Here are the results of cleaning my outliers and the cleaned-up variables:


![image](https://github.com/user-attachments/assets/e75420d2-c151-4264-8135-1c5caecdfa70)

![image](https://github.com/user-attachments/assets/aea98b78-7ef3-4b44-b066-76f0b70dbb2b)

![image](https://github.com/user-attachments/assets/5ca908c7-13ca-41f6-996c-bca698a1d754)

![image](https://github.com/user-attachments/assets/50799f28-4b6c-4eab-9f49-1c1339e82620)

![image](https://github.com/user-attachments/assets/d15a104b-770e-40f2-8f1d-25b4e3c81025)

![image](https://github.com/user-attachments/assets/85f95ca6-11b4-40c6-9914-419a15b2868b)

![image](https://github.com/user-attachments/assets/eda9c4c7-3c7b-4c8d-b87f-b2fa8bcfffa2)


D6: LIMITATIONS:

The methods I used to clean the data have some downsides. Dropping duplicates can make us lose important data and unbalance the dataset. Filling missing values with the mean for numbers can reduce variability and introduce bias, while using the mode for categories oversimplifies and can distort relationships. For outliers, using boxplots to find them, turning them into NAs, and then using the median can be subjective, change original values, and reduce variability. While these methods help prepare data for analysis, they can affect the accuracy and reliability of the results, leading to less accurate insights.

D7: IMPACT OF LIMITATIONS:

Even after I cleaned the data, there could still be problems affecting my research. Some data might still be missing or have hidden errors, and I might have removed some useful information by mistake. If I made many changes during cleaning and didn't document them well, it might be tough to understand the data fully. These problems can limit my analysis, make me less confident in my findings, and require more time and effort to address, which can complicate answering my research question.


E1: PRINCIPAL COMPONENTS:

In my PCA I used these variables: 'Income', 'Outage_sec_perweek', 'Tenure', 'MonthlyCharge', 'Bandwidth_GB_Year'. I used these values because I these are categorical variables and I can run a PCA on them.

![image](https://github.com/user-attachments/assets/212b4d9a-cd2c-434b-83d1-c2c585c9648c)


E2: CRITERIA USED:

I believe PC1, PC2 and PC3 should be retained because it is the only ones that has an eigenvalue of 1 or more, which according to the Kaiser Rule should be retained, while the other PCs are lower than 1. 
![image](https://github.com/user-attachments/assets/d229feba-51f5-4b14-9778-f79f1246d370)

E3: BENEFITS:

I believe the benefits of PCA is that it helps me simplify data, make better visualizations, reduce noise, improve model performance, and compress data. By focusing on the most important components, I can get clearer insights, make smarter decisions, and use resources more effectively. In my PCA example, focusing on components related to income, bandwidth usage, and monthly charges allows for more targeted and effective analysis, leading to better business results.


