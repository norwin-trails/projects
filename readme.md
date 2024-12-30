<style>
/* Style the GitHub Pages title */
.markdown-body h1:first-child {
  font-size: 2.5em !important;
  color: #002855 !important;
  font-weight: 600 !important;
  padding: 20px 0 !important;
  margin: 0 30px 20px !important;
  border-bottom: 3px solid #eaaa00 !important;
}

/* Style links */
.markdown-body a {
  color: #002855 !important;
  text-decoration: underline !important;
}

.markdown-body h1:first-child a {
  text-decoration: none !important;
}

.markdown-body a:hover {
  color: #eaaa00 !important;
}

/* Override GitHub Pages container width */
.markdown-body,
.markdown-body .container,
header.container,
div.container,
.container {
  max-width: none !important;
  width: 100% !important;
  padding: 0 30px !important;
  margin: 0 !important;
}

.markdown-body {
  box-sizing: border-box;
}

.container {
  display: flex !important;
  margin-bottom: 50px !important;
}

.info-panel {
  width: 30%;
  padding: 20px;
  box-sizing: border-box;
}

.map-container {
  width: 70%;
  box-sizing: border-box;
}

#map {
  height: 900px;
  width: 100%;
}
</style>

<div class="container">
  <div class="info-panel">
    <!-- Space for additional information -->
  </div>
  <div class="map-container">
    <div id="map"></div>
  </div>
</div>

<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />

<script>
  const map = L.map('map').setView([40.302799,-79.774776], 16);
  
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
  }).addTo(map);

  fetch('switch-board.geojson')
    .then(response => response.json())
    .then(data => {
      L.geoJSON(data, {
        style: {
          color: '#eaaa00',
          weight: 3,
          opacity: 0.85
        }
      }).addTo(map);
    });
</script>

### About
The [norwin-trails/braddocks-trail](https://github.com/norwin-trails/braddocks-trail) repository stores GIS data for Braddock's Trail Park.

All data was collected by [Friends of Norwin Trails](https://norwintrails.org), a 501(c)(3) organization committed to establishing safe and accessible recreational bicycling and walking opportunities in the Norwin area.