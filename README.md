# Home Sales Analysis

## Data and Cleaning

The dataset utilized was pulled from an ASW S3 bucket. The dataset included home sale data for homes built from 2011 - 2017 and sold between 2019 and 2022 in an unknown locality. The dataset includes the following information:

![image](https://github.com/rhisehl/Home_Sales/assets/116215793/b6bec201-dae9-4977-83b2-a05c04c44ae4)

The 'view' column is the rating of the views to the house listing. The 'year' column was added using the PySpark 'year' function.
The dataframe was imported  using pyspark and then moved into a temporary view for analysis.

## Analysis

The average price per year sold for 4+ bedroom houses:

![image](https://github.com/rhisehl/Home_Sales/assets/116215793/61e25d22-56ab-4b5a-9de6-6e83b9078269)


The average price per build year for 3+ bedroom and 3+ bathroom houses:

![image](https://github.com/rhisehl/Home_Sales/assets/116215793/8db995f3-f247-4443-bdab-2a8fa62e8b42)

The average price per build year for 3+ bedroom, 3+ bathroom, two-floor, 2,000+ sqft houses:

![image](https://github.com/rhisehl/Home_Sales/assets/116215793/a12a6904-32c4-4fa6-906c-a19b1c1371b2)

## Runtime Analysis

The next section involved determining the runtime for a query in three different conditions. The query was to determine the view ratings by average home price, where the average home price was at least $350,000.

![image](https://github.com/rhisehl/Home_Sales/assets/116215793/109b888a-8faa-4e0f-bc5f-b573c8fd4b3b)

### Condition 1: Running of normal, temporary table
Time: .722 seconds

### Condition 2: Running on cached version of temporary table
Time:  .405 seconds

## Condiiton 3: Running on a temporary view created by partitioning the data and converting the filet to a parquet format
Time: .707 seconds

Generally, partitioning should result in faster computation. It is possible that this dataset was not large enough to fully benefit from partitioning, or that there may be a better set of parameters for the partitioning. 
