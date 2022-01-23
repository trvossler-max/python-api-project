# Python-api-weather-vacation

This project uses python request, APIs, and JSON traversals to determine and visualize how weather changes as you approach the equater.  Scipy.stats is utilized to create linear regression visualiztion to determine any correlations between latitude and various weather impacts (cloudiness, humidity, temperature, wind speed). The next part of the project uses a new jupyter notebook and gmaps to created a map of cities with the best weather for vacation planning.

![Equator](Images/equatorsign.png)

## Part I - WeatherPy

Part 1 is a Python script to visualize the weather of 500+ cities across the world of varying distance from the equator. To accomplish this, I utilized a [simple Python library](https://pypi.python.org/pypi/citipy), the [OpenWeatherMap API](https://openweathermap.org/api), and a little common sense to create a representative model of weather across world cities.

This results in a series of scatter plots to showcase the following relationships:

* Temperature (F) vs. Latitude
* Humidity (%) vs. Latitude
* Cloudiness (%) vs. Latitude
* Wind Speed (mph) vs. Latitude

Next scipy.stats is used to run linear regression on each relationship, separating them into Northern Hemisphere (greater than or equal to 0 degrees latitude) and Southern Hemisphere (less than 0 degrees latitude):

* Northern Hemisphere - Temperature (F) vs. Latitude
* Southern Hemisphere - Temperature (F) vs. Latitude
* Northern Hemisphere - Humidity (%) vs. Latitude
* Southern Hemisphere - Humidity (%) vs. Latitude
* Northern Hemisphere - Cloudiness (%) vs. Latitude
* Southern Hemisphere - Cloudiness (%) vs. Latitude
* Northern Hemisphere - Wind Speed (mph) vs. Latitude
* Southern Hemisphere - Wind Speed (mph) vs. Latitude

### Part II - VacationPy

The second part of the project uses the weather data to plan future vacations. Jupyter-gmaps and the Google Places API is used for this part of the project.

* A heat map that displays the humidity for every city from the part I of the project.

  ![heatmap](Images/heatmap.png)

* The DataFrame narrowed down to find the ideal weather condition. For example:

  * A max temperature lower than 80 degrees but higher than 70.

  * Wind speed less than 10 mph.

  * Zero cloudiness.

* Google Places API is used to find the first hotel for each city located within 5000 meters of the coordinates.

* Hotels are plotted on top of the humidity heatmap with each pin containing the **Hotel Name**, **City**, and **Country**.

  ![hotel map](Images/hotel_map.png)

## Running the code

1. API keys will be needed in order to run the python scripts and should be in a file titled config.py for the Weatherpy python script and api_keys.py file for the VacationPy python script.

2. The Weatherpy python script must be run before the Vacationpy script in order to obtain the cities and weather data that will be used by Vacationpy.

