<!DOCTYPE html>
<html>
<head>
  <title>Share Your Location</title>
</head>
<body>
  <h2>Share Your Location</h2>
  <p>Click the button below to share your current location.</p>
  <button onclick="getLocation()">Share My Location</button>
  <p id="result"></p>

  <script>
    function getLocation() {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(showPosition, showError);
      } else {
        document.getElementById("result").innerText = "Geolocation is not supported by your browser.";
      }
    }

    function showPosition(position) {
      const lat = position.coords.latitude;
      const lon = position.coords.longitude;
      document.getElementById("result").innerText = 
        "Latitude: " + lat + "\nLongitude: " + lon;

      // Send to your server or Google Sheet
      console.log("Lat: " + lat + ", Lon: " + lon);
    }

    function showError(error) {
      document.getElementById("result").innerText = "Location access denied.";
    }
  </script>
</body>
</html>
