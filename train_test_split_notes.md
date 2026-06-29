# Train test split
## 70% train and 30% test

- cell 1
X = df.drop(columns=["default payment next month"])
y = df["default payment next month"]
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)
print("Training set size:", X_train.shape)
print("Test set size:", X_test.shape)
print("Training target size:", y_train.shape)
print(Test target size:", y_test.shape)

1. We split our DataFrame into features (X) and the target variable (y)

2. X = df.drop(columns=["default payment next month"]) removes the target variable to get the features

3. y = df["default payment next month"] takes only the target which is one singular column

4. Perform 70% train and 30% test split, meaning that 70% of the features and 70% of the target will be taken to train. Remaining 30% of the features and 30% of the target will be used for test.
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)
X_train is the 70% of the features that get sent for training
X_test is the remaining 30% of the features that will be hidden for testing
y_train is the 70% of the target that will be sent for training
y_test is the remaining 30% of the target that will be hidden for testing

5. 
print("Training set size:", X_train.shape) prints the rows and column of the 70% of features that got sent for training
print("Test set size:", X_test.shape) prints the rows and column of the remaining 30% of the features hidden for test
print("Training target size:", y_training.shape) prints the rows and columns of the 70% of target variables that got sent for training
print("Test target size:", y_test.shape) prints the rows and columns of the remaining 30% of target variables hidden for test


## Standardization
- cell 2
continuous_cols = ["LIMIT_BAL", "AGE", "PAY_AMT1", "PAY_AMT2", "PAY_AMT3", "PAY_AMT4", "PAY_AMT5", "PAY_AMT6", "BILL_AMT1", "BILL_AMT2", "BILL_AMT3", "BILL_AMT4", "BILL_AMT5", "BILL_AMT6"]

scaler = StandardScaler()
X_train[continuous_cols] = scaler.fit_transform(X_train[continuous_cols])
X_test[continuous_cols] = scaler.transform(X_test[continuous_Cols])
print("Standardization complete!")
print(X_train[continuous_cols].describe().round(2))

1. continuous_cols = [], continuous_cols becomes a list with all the column names
It can be used later on where df[continuous_cols] allows you to select multiple columns from the DataFrame.

2. scaler = StandardScaler()
StandardScaler() is a class which creates a scalar object and assign it to scaler

3. X_train[continuous_cols] = scaler.fit_transform(X_train[continuous_cols])
Basically we are now finding the mean and sd of each column using the values of the training set columns respectively, then we standardize it. Mean and SD are saved into the class scaler which is used to standardize values. Standardized values are not saved into the class.
scaler.fit_transform() can be split into scaler.fit() and scaler.transform()

4. X_test[continuous_cols] = scaler.transform(X_test[continuous_cols])
This uses the mean and SD of the training set to standardize the test set as to not leak anything from the hidden test. X_test X_train are all data frames that is why we can put [] next to it to search for specific columns


5. print(X_train[continuous_cols].describe().round(2))
This gives a summary for each of the columns selected for the dataframe showing sd mean and other useful variables while rounding decimal to 2 dp.