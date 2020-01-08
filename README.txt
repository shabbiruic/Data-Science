In this Project I build a model to predicte the mileage of different cars on a highways and in a cities.
Also also I have  build the classifier which classify the cars on the basis of transmission type i.e. manual and automatic.

I have used the cars Data set which has following attributes:

'Dimensions.Height','Dimensions.Length','DimensionsWidth','Engine Information.Engine Type', 'Engine Information.Driveline','Engine Information.Number of Forward Gears', 'Fuel Information.City mpg', 'Fuel Information.Highway mpg', 'Identification.ID','Identification.Make', 'Identification.Year', 'Fuel Information.Fuel Type','Identification.Classification', 'Engine Information.Engine Statistics.Horsepower','Engine Information.Engine Statistics.Torque','Engine Information.Driveline_Four-wheel drive','Engine Information.Driveline_Front-wheel drive','Engine Information.Driveline_Rear-wheel drive','Fuel Information.Fuel Type_Diesel fuel','Fuel Information.Fuel Type_E85','Fuel Information.Fuel Type_Gasoline','Identification.Classification_Manual transmission'

I have performed following steps to for building the predictor model:

Data Cleaning
In this, I have removed the data which is not relevant or is redundant. So I have removed
the following columns from our data:
	A. Engine Information Hybrid is a boolean column that has a value that is
	always true so it will be of no help in model building.
	B. Identification. Model Year this is redundant column as I have another
	column which provides this information which is Year
	C. Identification Make this is also not a car-related parameter rather its the
	name of the company which should not affect the mileage of a car.
	D. Engine Information. Engine Type this column is not atomic means it has
	more than one information inside it so I have extracted the information
	that is of our use and created a new column out of that like Number of
	cylinders a car has and then dropped this column.
	
Data Preparation
In this, I have converted the data in the form which is convenient for model building activity
and also which results in a better model.
	a. Standardized the data so that every attribute gets the same weight, for instance, the
	number of gears has a max value of 6 whereas torque can have values in hundreds so
	this normalization will help in building a model which gives equal importance to all
	attributes.
	b. Created separate columns for each categorical column like transmission which has a
	value either manual or automatic so that I can build a regression model out of this and
	also dropped one column out of all category columns created from that attribute to avoid
	the interdependency of columns.
	c. Used the holdout validation method for training and testing our model so I have split
	our dataset in the ratio of 75% for training and 25% for testing.
	d. Created a separated column out of Engine Information. Engine Type by just
	extracting only the number of cylinder information from this column by applying
	the python string function on that column.
	e. Renamed the column names into the more short and crisp form so that it
	becomes easy for further processing tasks.

Data Exploration
Created various plots to find the hidden pattern in the data set like which variable is correlated
with which all other variables. What are the various possible values of attributes. The range of
its values etc.
	Theses are the various plots that were created:
	a. Mileage and the number of cylinders car has
	b. Mileage of car vs the type of fuel car uses
	c. Mileage and the horsepower of the car engine
	d. the type of transmission car has and the mileage.
	e. Torque that car engine generates and the fuel mileage.
	f. Mileage and the driveline type of a car
	
Data Modeling
Linear Regression Model
Created multiple linear regression model using sklearn library I have used the scaled
variables and dummy columns created for categorical columns as the input to train our model
	For model predicting City Mileage
	Used the following variables as predictor variables along with their coefficient for predicting:
		Column Name Coefficient
		1. YearsOld : -0.18683432
		2. FuelType_Diesel: 3.70863877
		3. FuelType_E85: -5.66003664
		4. FuelType_Gasoline: -0.95081266
		5. Classification_ManualTransmission : 1.00368165
		6. Horsepower: 0.25799251
		7. Torque: -1.37231489
		8. Cylinder: -1.46323227
		9. Four-wheelDrive: -0.88850086
		10. Front-wheelDrive: 2.33837197
		11. Rear-wheelDrive: 0.18759773
		12. DimensionsHeight: 0.16111597
		13. DimensionsLength: 0.027655
		14. DimensionsWidth: 0.28169426
	Model Parameters I got are :
	R squared: 0.8240537211373345
	Adjusted R square: 0.8220831228140727
	
	For model predicting Highway Mileage
	Used the following variables as predictor variables along with their coefficient for predicting:
		Column Name Coefficient
		1. YearsOld: -0.36848049
		2. FuelType_Diesel: 2.30535562
		3. FuelType_E85: -11.49813727
		4. FuelType_Gasoline: -5.15801274
		5. Classification_ManualTransmission : 1.23059854
		6. Horsepower: 1.68277827
		7. Torque: -2.2707133
		8. Cylinder: -2.15449565
		9. Four-wheelDrive: -1.96267892
		10. Front-wheelDrive: 3.59795013
		11. Rear-wheelDrive: 0.52176918
		12. DimensionsHeight: 0.29797584
		13. DimensionsLength: 0.14418514
		14. DimensionsWidth: 0.17706032
	Model Parameters I got are :
	R squared: 0.792964654392592
	Adjusted R square: 0.7921978568162682
