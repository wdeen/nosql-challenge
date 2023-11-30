# nosql-challenge
Module 12 Challenge (NoSQL) - Wassim Deen

# Scenario Description
The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

# Summary of Challenge
- Part 1: Database and Jupyter Notebook Set Up (`NoSQL_setup.ipynb`)
    1. Import the data provided in the `establishments.json` file from my Terminal (Gitbash). Name the database `uk_food` and the `collection` establishments. Copy the text I used to import your data from my Terminal (Gitbash) to a markdown cell in my Jupyter Notebook solution file.

    2. Within my Jupyter Notebook solution file, import the following libraries: PyMongo and Pretty Print (`pprint`).

    3. Create an instance of the Mongo Client.

    4. Confirm that I created the database and loaded the data properly:
        - List the databases in my local MongoDB server. Confirm that `uk_food` is listed.
        - List the collection(s) in the database to ensure that `establishments` is there.
        - Find and display one document in the `establishments` collection using `find_one` and display with `pprint`.

    5. Assign the `establishments` collection to a variable to prepare the collection for use.

- Part 2: Update the Database (`NoSQL_setup.ipynb`)

  The magazine editors have some requested modifications for the database before you can perform any queries or analysis for them. Make the following changes to the `establishments` collection:

  1. An exciting new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine has asked me to include it in your analysis. Add the following information to the database:

            {
                "BusinessName":"Penang Flavours",
                "BusinessType":"Restaurant/Cafe/Canteen",
                "BusinessTypeID":"",
                "AddressLine1":"Penang Flavours",
                "AddressLine2":"146A Plumstead Rd",
                "AddressLine3":"London",
                "AddressLine4":"",
                "PostCode":"SE18 7DY",
                "Phone":"",
                "LocalAuthorityCode":"511",
                "LocalAuthorityName":"Greenwich",
                "LocalAuthorityWebSite":"http://www.royalgreenwich.gov.uk",
                "LocalAuthorityEmailAddress":"health@royalgreenwich.gov.uk",
                "scores":{
                    "Hygiene":"",
                    "Structural":"",
                    "ConfidenceInManagement":""
                },
                "SchemeType":"FHRS",
                "geocode":{
                    "longitude":"0.08384000",
                    "latitude":"51.49014200"
                },
                "RightToReply":"",
                "Distance":4623.9723280747176,
                "NewRatingPending":True
            }

  
    2. Find the BusinessTypeID for "Restaurant/Cafe/Canteen" and return only the `BusinessTypeID` and `BusinessType` fields.
    
    3. Update the new restaurant with the `BusinessTypeID` you found.
    
    4. The magazine is not interested in any establishments in Dover. Check how many documents contain the Dover Local Authority. Then, remove any establishments within the Dover Local Authority from the database, and check the number of documents to ensure they were deleted.

    5. Some of the number values are stored as strings, when they should be stored as numbers:
         - Use `update_many` to convert `latitude` and `longitude` to decimal numbers.
         - Use `update_many` to convert `RatingValue` to integer numbers.

- Part 3: Exploratory Analysis (`NoSQL_analysis.ipynb`)

  Eat Safe, Love has specific questions they want me to answer, which will help them find the locations they wish to visit and avoid.


  Ahead of this, the following notes were considered while exploring the dataset:

      RatingValue refers to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating.

  <strong>Note:</strong> This field also includes non-numeric values such as 'Pass', where 'Pass' means that the establishment passed their inspection but isn't given a number rating. We will coerce non-numeric values to nulls during the database setup before converting ratings to integers.
        
        The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse. This means, the higher the value, the worse the establishment is in these areas.        
        
    Unless otherwise stated, for each question:
    - Use `count_documents` to display the number of documents contained in the result.
    - Display the first document in the results using `pprint`.
    - Convert the result to a Pandas DataFrame, print the number of rows in the DataFrame, and display the first 10 rows.

    The questions below were used to explore the database.

    1. Which establishments have a `Hygiene` score equal to 20?

    2. Which establishments in London have a `RatingValue` greater than or equal to 4?

    3. What are the top 5 establishments with a `RatingValue` of '5', sorted by lowest `Hygiene` score, nearest to the new restaurant added, "Penang Flavours"?

    4. How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.


# Final Repository Structure
```
├── README.md
├── NoSQL_analysis.ipynb
├── NoSQL_setup.ipynb
├── .DS_Store
└── Resources
    ├── establishments.json


```
