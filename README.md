# TechPoint Xtern Data Science Work Sample Assessment

** TO VIEW JUPYTER NOTEBOOK WITH MAPS, CLICK HERE: https://nbviewer.org/github/ryangoldfeder21/TechPoint-Xtern-Data-Science-Work-Sample-Assessment/blob/main/Ryan_Goldfeder_Techpoint_Xtern_Work_Sample_Data_Science.ipynb**
 
For the Techpoint Xtern data science work sample assessment, I was tasked with using an Open Source API to find information about food trucks in Indianapolis, creating a weekend travel plan to visit some of those food trucks, and designing a map to illustrate the weekend travel plan. Throughout this project, I used various tools, including Google Maps API, Yelp API, and the python map library Folium. Overall, I was successfully able to create a dataframe with food truck data, a dataframe with the weekend plan, and two maps with the Saturday and Sunday travel routes. Below, I will list each of the seven steps I took to complete this project, and include descriptions of my thinking and process.


1. Setting Up Google Map API

I chose to begin this project by using Google Maps API. In order to set up the API, I created an account in google developer, acquired a free API key, and used that API key to create a google maps client variable that can call all of the necessary API functions.


2. Searching for Food Trucks

The first step to complete this project was creating a dataframe. Before I could create a dataframe, however, I needed to use the API to find food trucks and the necessary information. I was able to use the places_nearby function, with keywords and location as parameters, in order to find food trucks near Indianapolis. Additionally, I used the .place function with the place id as one of the parameters in order to acquire details about the food truck. This allowed me to find information about the food truck’s website and opening hours, in addition to the already provided name, address, and rating. Cuisine information was not included, however. Regarding opening hours, since there were several format types within the parameter, I used indexing to extract a string that included all of the information about a food truck’s hours.


3. Creating Dataframe with Food Truck Information

Each places_nearby function call only returned 20 results, so I had to use the next_page_token to get more results. I was able to do this three times and get 60 food trucks in total. To fill in the dataframe, I created lists for each column and looped through each food truck, adding all of the necessary categories to the lists. I then set each column of the dataframe to the respective lists. Finally, I sorted the dataframe by rating, so the highest rated trucks would occur first in the table.


4. Finding Cuisine of a Food Truck

Since Google Maps API does not include cuisine data, I had to find a second API to search for this category. To do so, I set up the Yelp API, and used the food truck names and addresses to find the same food trucks in Yelp. This API included a variable called “categories”, which contained some cuisine data. To extract the cuisine variable, I looped through categories and added each category to a string variable, separated by commas. Some of these categories were ‘Food Trucks’ and ‘Caterers’, so I added an if condition to not include these strings in cuisine. While this method was effective for some of the food trucks, Yelp API could not find most of the food trucks when searching. As a result, most of the cuisine values ended up being ‘NA’. If I had more time to complete this project, I would find another API to search for cuisine more accurately.


5. Choosing Food Trucks and Times to Visit

By sorting the data frame by rating, I was able to search down the list of food trucks and pick the 10 highest-rated trucks to visit that also included opening hours. Because I needed to make a schedule, I neglected food trucks with a null value for opening hours. I decided to set the meal times at 12, 3, 6, 7, and 10 PM, which allowed for a lunch, snack, 2 dinner options, and a late night snack (most trucks were not open for breakfast). Among the ten food trucks chosen, I selected the times based on opening hours, and whether they were closed on Sundays, to ensure that every truck was open when visiting. Later on, I modified this schedule to reduce travel time after seeing the maps and determining which food trucks were closer together.


6. Finding Travel Details and Creating a Second DataFrame

To finish filling out the second dataframe, I used the first dataframe and the food truck names to extract and fill out the address variable. To find the travel distance, time, and transportation type, I used Directions API and found variables that tracked these characteristics. Driving was the transportation type chosen throughout because most food trucks were miles apart. To set travel distance and time, I obtained directions from the previous food truck to the current truck in the list, using IUPUI as a starting point for each day. Even though there are hours in between some of the meals, I used the previous truck as a starting point for reference and assumed that the group would not go anywhere else besides the food trucks (even though this would be different in reality). Additionally, since cuisine data was missing for all of the ten food trucks that I chose, I filled it out manually in this second dataframe.


7. Creating a Travel Route Map

The final step of this project was creating a map that illustrated where the group would be traveling and in what order. I chose to use the Folium library to plot two maps: one for Saturday and one for Sunday. Using this library, I was able to plot a map with circles representing the food trucks and lines representing the order of the food trucks. I added icons that if clicked on, displayed the food truck name and visit time. If I had more time for this project, I would modify the lines to display the specific driving route instead of just being a straight line.


Conclusion
Overall, the travel plan and maps will allow the group to visit most of the five-star food trucks around Indianapolis and have a blast! The time schedule allows for sleeping in and having free time to explore in between stops. Because time constraints (2 day weekend) were more significant than cost constraints (easy access to a car assumed), the group can visit food trucks in all corners of Indianapolis.
A couple of other observations I made are that reviews are heavily skewed toward 4 and 5 stars, and there are very few 1 and 2 star trucks. This makes sense, as low-quality food trucks will not stay open for that long. Additionally, many of the food trucks are closed on Sundays and on Saturday morning, so it was harder to find trucks that were open then. However, with an abundance of 5 star trucks, there are still plenty to visit on Sundays.
In addition to this project description, included in this GitHub repository is the Google Colab Jupyter Notebook, the data csv file, and the travel plan csv file.
