# leaflet-opencage-geocoding-and-geosearch-samples.git

## Objective

How to use [OpenCage Geocoding Control for Leaflet](https://github.com/OpenCageData/leaflet-opencage-geocoding).

## Geocoding usage with Leaflet 1.x

Load LeafletJS 1.x CSS and Javascript files:

```html
<link
  rel="stylesheet"
  href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
/>
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet-src.js"></script>
```

Load the plugin's CSS and JavaScript files:

```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/gh/opencagedata/leaflet-opencage-geocoding@v2.0.0/dist/css/L.Control.OpenCageGeocoding.min.css"
/>
<script src="https://cdn.jsdelivr.net/gh/opencagedata/leaflet-opencage-geocoding@v2.0.0/dist/js/L.Control.OpenCageGeocoding.min.js"></script>
```

Create a map

```js
const map = L.map('map').setView([51.52255, -0.10249], 13);
const tiles = new L.TileLayer(
  'https://tile.openstreetmap.org/{z}/{x}/{y}.png',
  {
    maxZoom: 19,
    attribution:
      '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
  }
).addTo(map);
```

Then add the plugin

```js
const options = {
  key: 'your-api-key-here',
  limit: 10,
};
const control = L.Control.openCageGeocoding(options).addTo(map);
```

Test it with `open geocoding_leaflet-1.x.html`, don't forget to set your API key

## Geocoding usage with Leaflet 2.0.0-alpha

Leaflet 2 support ESM and tree shaking, check the new feature on the announcement [page](https://leafletjs.com/2025/05/18/leaflet-2.0.0-alpha.html). The major change is the global L is no longer part of the core package, though it’s still available in the bundled version leaflet-global.js for backward compatibility.

### Using Global Script and v1 Polyfill

This is the easiest way to keep an existing application working with LeafletJS 2.0

Load LeafletJS 2.x CSS and Javascript files:

```html
<link
  rel="stylesheet"
  href="https://unpkg.com/leaflet@2.0.0-alpha/dist/leaflet.css"
/>
<script src="https://unpkg.com/leaflet@2.0.0-alpha/dist/leaflet-global.js"></script>
```

Download the file [leaflet-v1-polyfill.js](./leaflet-v1-polyfill.js) from https://github.com/Falke-Design/Leaflet-V1-polyfill and add it to your scripts.

```html
<script src="./leaflet-v1-polyfill.js"></script>
```

The Javascript code to use the plugin is almost the same then, we only need to add the polyfills

```js
applyAllPolyfills();
```

this allow to keep the same code as with LeafletJS v1.x

```js
const map = new L.Map('map').setView([51.505, -0.09], 13);

const tiles = new L.TileLayer(
  'https://tile.openstreetmap.org/{z}/{x}/{y}.png',
  {
    maxZoom: 19,
    attribution:
      '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
  }
).addTo(map);

const options = {
  key: 'your-api-key-here',
  limit: 10,
};
const control = L.Control.openCageGeocoding(options).addTo(map);
```

Test it with `open geocoding_leaflet-2.x-global-script.html`, don't forget to set your API key

## Geosearch usage with Leaflet 1.x

Test it with `open geosearch_leaflet-1.x.html`, don't forget to set your Geosearch key

## Geosearch usage with Leaflet 2.0.0-alpha

Test it with `open geosearch_leaflet-2.x-global-script.html`, don't forget to set your Geosearch key
