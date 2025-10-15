# sql-data-clearning
Using SQL to clearn data
<img alt="image" data-start="155" data-end="244" src="https://github.com/user-attachments/assets/9ab3e675-e6d3-415e-8ec3-7666485fbb6f">
This is an educational project on data cleaning and preparation using SQL. The original database in CSV format is located in the file club_member_info.csv. Here, we will explore the steps that need to be applied to obtain a cleansed version of the dataset.
## 1. View Data
```
SELECT * FROM club_member_info cmi 
LIMIT  5;
```
|full_name|age|martial_status|email|phone|full_address|job_title|membership_date|
|---------|---|--------------|-----|-----|------------|---------|---------------|
|addie lush|40|married|alush0@shutterfly.com|254-389-8708|3226 Eastlawn Pass,Temple,Texas|Assistant Professor|7/31/2013|
|      ROCK CRADICK|46|married|rcradick1@newsvine.com|910-566-2007|4 Harbort Avenue,Fayetteville,North Carolina|Programmer III|5/27/2018|
|Sydel Sharvell|46|divorced|ssharvell2@amazon.co.jp|702-187-8715|4 School Place,Las Vegas,Nevada|Budget/Accounting Analyst I|10/6/2017|
|Constantin de la cruz|35||co3@bloglines.com|402-688-7162|6 Monument Crossing,Omaha,Nebraska|Desktop Support Technician|10/20/2015|
|  Gaylor Redhole|38|married|gredhole4@japanpost.jp|917-394-6001|88 Cherokee Pass,New York City,New York|Legal Assistant|5/29/2019|

```
CREATE TABLE club_member_info_cleaned (
	full_name VARCHAR(50),
	age INTEGER,
	martial_status VARCHAR(50),
	email VARCHAR(50),
	phone NVARCHAR(50),
	full_address NVARCHAR(50),
	job_title VARCHAR(50),
	membership_date NVARCHAR(50)
);
```
## 2. Clearning Data
```
INSERT INTO club_member_info_cleaned 
SELECT * FROM club_member_info 
```
### Duplicate Count
```
SELECT full_name,
age,
martial_status,
email,
phone,
full_address,
job_title,
membership_date,
COUNT(*) AS duplicate_count
FROM club_member_info_cleaned
GROUP BY full_name,age,
martial_status,
email,
phone,
full_address,
job_title,
membership_date
HAVING COUNT(*) > 1;
```

