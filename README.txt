Used Google Places API with Database and Visualizing Data on Google Map

This project utilizes the Google Places API to refine user-entered geographic locations of universities and then displays the data on a Google Map.

**Note**: If you're using Windows, displaying UTF-8 characters in the console may be challenging. For each command window opened, execute the following command before running the code:

```
chcp 65001
```

For more details, refer to: [Unicode Characters in Windows Command Line](http://stackoverflow.com/questions/388490/unicode-characters-in-windows-command-line-how)

## Requirements

Ensure you have installed SQLite browser to view and modify databases from [sqlitebrowser.org](http://sqlitebrowser.org/).

## Project Overview

The primary challenge lies in the rate limit imposed by the Google geocoding API, restricting the number of requests per day. To overcome this, the project is divided into two phases.

### Phase 1: Geocoding and Database Population

- Input data is stored in the file `where.data`.
- The `geoload.py` program reads the data line by line, checks if the data is already present in the database (`geodata.sqlite`), and if not, retrieves the geocoded response and stores it in the database.

### Phase 2: Visualization

Once the database (`geodata.sqlite`) is populated:

- Execute the `geodump.py` program to read the database and generate a JavaScript file (`where.js`) containing location data in the format of executable JavaScript code.
- The `where.html` file consists of HTML and JavaScript to visualize a Google Map using the data from `where.js`.

## Using the Google Geocoding API

As of December 2016, Google significantly updated its Geocoding APIs, shifting some functionalities to the Places API. Additionally, an API key is now required for all Google Geo-related APIs. However, you can access a subset of the data without an API key from:

[http://py4e-data.dr-chuck.net/json](http://py4e-data.dr-chuck.net/json)

To use this subset, set `api_key` to `False` in `geoload.py`. This URL has no rate limit and is suitable for testing.

For API key usage instructions, refer to [Google Maps Geocoding API Documentation](https://developers.google.com/maps/documentation/geocoding/intro).

## Sample Run

After the database is populated, running `geodump.py` generates location data. Open `where.html` in a browser to view the locations on a Google Map. Hover over each map pin to view the geocoded location returned by the API.

## File Formats

- **`where.js`**: Contains location data in JavaScript list of lists format.
- **`where.html`**: HTML and JavaScript file to visualize data on a Google Map.

## Running the Programs

- To run `geoload.py`:
  - Mac: `python3 geoload.py`
  - Windows: `geoload.py`
  
- To run `geodump.py`:
  - Mac: `python3 geodump.py`
  - Windows: `geodump.py`

Ensure the SQLite browser is installed to view and manage the database effectively.

For further assistance or debugging, check the JavaScript or developer console in your browser.

Enjoy exploring the visualized data on the Google Map!
