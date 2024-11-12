# Documentation for Wikipedia Search Project

## Overview

The "Wikipedia Viewer" project is a web application that allows users to search Wikipedia directly from the webpage. It uses jQuery to fetch and display results from the Wikipedia API in real-time as users enter search queries.

## Table of Contents

1. Project Structure
2. HTML Structure
3. CSS Styling
4. JavaScript Functionality
5. How to Use
6. Contribution
7. License

## 1. Project Structure

- `index.html`: Contains the basic HTML structure of the search interface.
- `styles.css`: Contains the styling for the webpage, including input boxes and result containers.
- `app.js`: Contains the logic to handle search queries and make requests to the Wikipedia API.

## 2. HTML Structure

### Key Elements:

- **Search Input Box**: Allows the user to input a search query.
  ```html
  <div id="searchBox">
      <input type="text" 
             id="search" 
             autocomplete="off" 
             placeholder="Search here" />
  </div>

Headings: Displays the title of the webpage.

<h1 id="top">
    Search @ Wikipedia
</h1>
<h1>
    Wikipedia Viewer
</h1>

Scripts and Stylesheets: Links to external stylesheet and jQuery library, along with the JavaScript file.

<link rel="stylesheet" type="text/css" href="styles.css" />
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
<script src="app.js" type="text/javascript"></script>



---

## 3. CSS Styling

Key Styles:

Body and General Elements: Centers text and sets default styles.

body {
    text-align: center;
}

#top {
    color: green;
}

h1 {
    margin-top: 30px;
}

Search Box Styling: Styles the search input box with rounded corners, animations, and text alignment.

input[type="text"] {
    border-radius: 15px;
    text-align: center;
    height: 50px;
    width: 600px;
    -webkit-transition: width 0.4s ease-in-out;
    transition: width 0.4s ease-in-out;
}

input[type="text"]:focus {
    width: 100%;
}

Search Results Styling: Styles the display and hover behavior for search results.

.searchResult {
    background-color: rgb(153, 225, 155);
    color: rgb(18, 17, 17);
    height: 60px;
    padding: 10px;
    margin: 2px;
}

.searchResult:hover {
    cursor: pointer;
    background-color: white;
    color: black;
}

## 4. JavaScript Functionality

Key Features:

Search on Enter Key: Initiates a search request to the Wikipedia API when the Enter key is pressed.

$(document).keypress(function (e) {
    if (e.which == 13) {
        let webLink = "...api.php?action=query&list=search&srsearch=" +
            document.getElementById("search").value +
            "&utf8=&format=json";
        $.ajax({
            url: webLink,
            dataType: "jsonp",
            success: function (data) {
                $("div").remove(".searchResult");
                for (i = 0; i < data.query.search.length; i++) {
                    let titleForResult = data.query.search[i].title;
                    let snippetForResult = data.query.search[i].snippet;
                    $("#searchBox").append(
                        '<a href="https://example.com/' +
                        titleForResult +
                        `" target="_blank" style="text-decoration:none">
                            <div class="searchResult">
                            <span class="searchTitle">` +
                        titleForResult +
                        "</span><span><br />" +
                        snippetForResult +
                        "</span></div></a>"
                    );
                }
            },
        });
    }
});

AJAX Request: Makes an asynchronous request to the Wikipedia API and retrieves results based on the user's input.

$.ajax({
    url: webLink,
    dataType: "jsonp",
    success: function (data) {
        $("div").remove(".searchResult");
        for (i = 0; i < data.query.search.length; i++) {
            // Appends each search result to the page
        }
    },
});

## 5. How to Use

1. Open the webpage.


2. Enter a search term in the input box.


3. Press "Enter" to see the results retrieved from the Wikipedia API.


4. Click on a result to be redirected to the corresponding page.


## 6. Contribution

If you wish to contribute to this project, feel free to:

Fork the repository.

Create a new branch (git checkout -b feature-branch).

Commit your changes (git commit -m "Description of changes").

Push to the branch (git push origin feature-branch).

Create a pull request for review.

## 7. License

This project is open-source and available under the MIT License.

Now, you can copy and paste this documentation directly into your `README.md` file or any documentation file for easy reference.

