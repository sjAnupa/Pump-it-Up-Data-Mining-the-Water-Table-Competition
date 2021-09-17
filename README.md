# Pump-it-Up-Data-Mining-the-Water-Table-Competition

## Basics

Repository : https://github.com/sjAnupa/Pump-it-Up-Data-Mining-the-Water-Table-Competition

Used Model: RandomForest Classifier [Tested for RandomForest Classifier, LogisticRegression, DecisionTreeClassifier]

Competetion Link: https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/

## Preprocessing

### Removed Columns

 Target values were highly imbalanced. Also, there were some null values and some columns which contained same information in the data set. Some columns didn't affeted for the target values. So columns which had those similarities were dropped.
 
 Dropped Columns:
 -  management_group
 -  scheme_management
 -  quantity_group
 -  source_class
 -  source_type
 -  quality_group
 -  payment_type
 -  extraction_type_class
 -  extraction_type
 -  waterpoint_type_group

Created a new dataset called `decade` using `construction_year` which years were converted to decades they belongs.

`recorded_by` column had only one value which is 'GeoData Consultants Ltd '. therefore, column was dropped.

Due to high amount of Nan and 0 values in`installer` column, all the data converted to Unknown. Sililar data identified which belongs to same category, differs due to spelling mistake. Most of them were fixed.

Created a new column `installer_cat` using `installer` column, getting mostly affected columns. `installer` column was dropped later.

In `funder` column, took most 20 categories and created a new column `funder_cat`.

All the 0 values were replaced with mean `longitude` and `latitude` values in columns.

`wpt_name`,`scheme_name`,`id` columns didn't had any info about functionality. Therefore those columns were dropped. And `region_code`,`subvillage` had same value in `region`. So those were dropped.

`amount_tsh` column were dropped due to 70% of the values didn't had informative information.

Approximately 95% of the water points were recorded between 2011-2013. Therefore `date_recorded` column was dropped. `num_private` was also dropped due to not having informatieve data.

All the Nan values in `public_meeting`,`permit` were converted to most common data.

### Model
Minmax scaler used to encode numeric columns. Onehot Encoder used to encode categorical columns. Tested for following classifiers and Selected RandomForest Classifier which had higher acuracy.
- RandomForest Classifier
- LogisticRegression
- DecisionTreeClassifier


Accuracy:

TRAIN: 0.9030303030303031

TEST: 0.7888888888888889

Output csv file for test value data set was archived 0.8160 acuracy with the rank of 1776 in the competetion. 

![Image](https://github.com/sjAnupa/Pump-it-Up-Data-Mining-the-Water-Table-Competition/blob/main/Final%20Rank.PNG)

