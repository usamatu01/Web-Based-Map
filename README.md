<!doctype html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="initial-scale=1,user-scalable=no,maximum-scale=1,width=device-width">
        <meta name="mobile-web-app-capable" content="yes">
        <meta name="apple-mobile-web-app-capable" content="yes">
        <link rel="stylesheet" href="css/leaflet.css"><link rel="stylesheet" href="css/L.Control.Locate.min.css">
        <link rel="stylesheet" href="css/qgis2web.css"><link rel="stylesheet" href="css/fontawesome-all.min.css">
        <link rel="stylesheet" href="css/leaflet-search.css">
        <link rel="stylesheet" href="css/leaflet-control-geocoder.Geocoder.css">
        <link rel="stylesheet" href="css/leaflet-measure.css">
        <style>
        html, body, #map {
            width: 100%;
            height: 100%;
            padding: 0;
            margin: 0;
        }
        </style>
        <title></title>
    </head>
    <body>
        <div id="map">
        </div>
        <script src="js/qgis2web_expressions.js"></script>
        <script src="js/leaflet.js"></script><script src="js/L.Control.Locate.min.js"></script>
        <script src="js/multi-style-layer.js"></script>
        <script src="js/leaflet.rotatedMarker.js"></script>
        <script src="js/leaflet.pattern.js"></script>
        <script src="js/leaflet-hash.js"></script>
        <script src="js/Autolinker.min.js"></script>
        <script src="js/rbush.min.js"></script>
        <script src="js/labelgun.min.js"></script>
        <script src="js/labels.js"></script>
        <script src="js/leaflet-control-geocoder.Geocoder.js"></script>
        <script src="js/leaflet-measure.js"></script>
        <script src="js/proj4.js"></script>
        <script src="js/proj4leaflet.js"></script>
        <script src="js/leaflet-search.js"></script>
        <script src="data/AcadamicsFacilities_0.js"></script>
        <script src="data/MinorRoad_1.js"></script>
        <script src="data/ReligiosStructures_2.js"></script>
        <script src="data/HealthFacilities_3.js"></script>
        <script src="data/ProminantFeatures_4.js"></script>
        <script src="data/BOUNDRY_5.js"></script>
        <script src="data/MajorRoad_6.js"></script>
        <script>
        var highlightLayer;
        function highlightFeature(e) {
            highlightLayer = e.target;

            if (e.target.feature.geometry.type === 'LineString') {
              highlightLayer.setStyle({
                color: '#ffff00',
              });
            } else {
              highlightLayer.setStyle({
                fillColor: '#ffff00',
                fillOpacity: 1
              });
            }
            highlightLayer.openPopup();
        }
        var crs = new L.Proj.CRS('EPSG:3395', '+proj=merc +lon_0=0 +k=1 +x_0=0 +y_0=0 +datum=WGS84 +units=m +no_defs', {
            resolutions: [2800, 1400, 700, 350, 175, 84, 42, 21, 11.2, 5.6, 2.8, 1.4, 0.7, 0.35, 0.14, 0.07],
        });
        var map = L.map('map', {
            crs: crs,
            continuousWorld: false,
            worldCopyJump: false, 
            zoomControl:true, maxZoom:28, minZoom:1
        }).fitBounds([[10.504191730209838,7.386863654016418],[10.52580646353736,7.4271400304980375]]);
        var hash = new L.Hash(map);
        map.attributionControl.setPrefix('<a href="https://github.com/tomchadwin/qgis2web" target="_blank">qgis2web</a> &middot; <a href="https://leafletjs.com" title="A JS library for interactive maps">Leaflet</a> &middot; <a href="https://qgis.org">QGIS</a>');
        var autolinker = new Autolinker({truncate: {length: 30, location: 'smart'}});
        L.control.locate({locateOptions: {maxZoom: 19}}).addTo(map);
        var measureControl = new L.Control.Measure({
            position: 'topleft',
            primaryLengthUnit: 'meters',
            secondaryLengthUnit: 'kilometers',
            primaryAreaUnit: 'sqmeters',
            secondaryAreaUnit: 'hectares'
        });
        measureControl.addTo(map);
        document.getElementsByClassName('leaflet-control-measure-toggle')[0]
        .innerHTML = '';
        document.getElementsByClassName('leaflet-control-measure-toggle')[0]
        .className += ' fas fa-ruler';
        var bounds_group = new L.featureGroup([]);
        function setBounds() {
            map.setMaxBounds(map.getBounds());
        }
        function pop_AcadamicsFacilities_0(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <th scope="row">id</th>\
                        <td>' + (feature.properties['id'] !== null ? autolinker.link(feature.properties['id'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['schools'] !== null ? autolinker.link(feature.properties['schools'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_AcadamicsFacilities_0_0() {
            return {
                pane: 'pane_AcadamicsFacilities_0',
        rotationAngle: 0.0,
        rotationOrigin: 'center center',
        icon: L.icon({
            iconUrl: 'markers/sport_snooker.svg',
            iconSize: [17.479999999999997, 17.479999999999997]
        }),
                interactive: true,
            }
        }
        map.createPane('pane_AcadamicsFacilities_0');
        map.getPane('pane_AcadamicsFacilities_0').style.zIndex = 400;
        map.getPane('pane_AcadamicsFacilities_0').style['mix-blend-mode'] = 'normal';
        var layer_AcadamicsFacilities_0 = new L.geoJson(json_AcadamicsFacilities_0, {
            attribution: '',
            interactive: true,
            dataVar: 'json_AcadamicsFacilities_0',
            layerName: 'layer_AcadamicsFacilities_0',
            pane: 'pane_AcadamicsFacilities_0',
            onEachFeature: pop_AcadamicsFacilities_0,
            pointToLayer: function (feature, latlng) {
                var context = {
                    feature: feature,
                    variables: {}
                };
                return L.marker(latlng, style_AcadamicsFacilities_0_0(feature));
            },
        });
        bounds_group.addLayer(layer_AcadamicsFacilities_0);
        map.addLayer(layer_AcadamicsFacilities_0);
        function pop_MinorRoad_1(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <th scope="row">id</th>\
                        <td>' + (feature.properties['id'] !== null ? autolinker.link(feature.properties['id'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['ROAD'] !== null ? autolinker.link(feature.properties['ROAD'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_MinorRoad_1_0() {
            return {
                pane: 'pane_MinorRoad_1',
                opacity: 1,
                color: 'rgba(0,0,0,1.0)',
                dashArray: '',
                lineCap: 'round',
                lineJoin: 'round',
                weight: 4.0,
                fillOpacity: 0,
                interactive: true,
            }
        }
        function style_MinorRoad_1_1() {
            return {
                pane: 'pane_MinorRoad_1',
                opacity: 1,
                color: 'rgba(255,255,255,1.0)',
                dashArray: '',
                lineCap: 'round',
                lineJoin: 'round',
                weight: 3.0,
                fillOpacity: 0,
                interactive: true,
            }
        }
        map.createPane('pane_MinorRoad_1');
        map.getPane('pane_MinorRoad_1').style.zIndex = 401;
        map.getPane('pane_MinorRoad_1').style['mix-blend-mode'] = 'normal';
        var layer_MinorRoad_1 = new L.geoJson.multiStyle(json_MinorRoad_1, {
            attribution: '',
            interactive: true,
            dataVar: 'json_MinorRoad_1',
            layerName: 'layer_MinorRoad_1',
            pane: 'pane_MinorRoad_1',
            onEachFeature: pop_MinorRoad_1,
            styles: [style_MinorRoad_1_0,style_MinorRoad_1_1,]
        });
        bounds_group.addLayer(layer_MinorRoad_1);
        map.addLayer(layer_MinorRoad_1);
        function pop_ReligiosStructures_2(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['id'] !== null ? autolinker.link(feature.properties['id'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['Mosque'] !== null ? autolinker.link(feature.properties['Mosque'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_ReligiosStructures_2_0() {
            return {
                pane: 'pane_ReligiosStructures_2',
        rotationAngle: 0.0,
        rotationOrigin: 'center center',
        icon: L.icon({
            iconUrl: 'markers/place_of_worship_islamic3.svg',
            iconSize: [12.16, 12.16]
        }),
                interactive: true,
            }
        }
        map.createPane('pane_ReligiosStructures_2');
        map.getPane('pane_ReligiosStructures_2').style.zIndex = 402;
        map.getPane('pane_ReligiosStructures_2').style['mix-blend-mode'] = 'normal';
        var layer_ReligiosStructures_2 = new L.geoJson(json_ReligiosStructures_2, {
            attribution: '',
            interactive: true,
            dataVar: 'json_ReligiosStructures_2',
            layerName: 'layer_ReligiosStructures_2',
            pane: 'pane_ReligiosStructures_2',
            onEachFeature: pop_ReligiosStructures_2,
            pointToLayer: function (feature, latlng) {
                var context = {
                    feature: feature,
                    variables: {}
                };
                return L.marker(latlng, style_ReligiosStructures_2_0(feature));
            },
        });
        bounds_group.addLayer(layer_ReligiosStructures_2);
        map.addLayer(layer_ReligiosStructures_2);
        function pop_HealthFacilities_3(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['id'] !== null ? autolinker.link(feature.properties['id'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['Hospital'] !== null ? autolinker.link(feature.properties['Hospital'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_HealthFacilities_3_0() {
            return {
                pane: 'pane_HealthFacilities_3',
        rotationAngle: 0.0,
        rotationOrigin: 'center center',
        icon: L.icon({
            iconUrl: 'markers/health_doctors.svg',
            iconSize: [12.16, 12.16]
        }),
                interactive: true,
            }
        }
        map.createPane('pane_HealthFacilities_3');
        map.getPane('pane_HealthFacilities_3').style.zIndex = 403;
        map.getPane('pane_HealthFacilities_3').style['mix-blend-mode'] = 'normal';
        var layer_HealthFacilities_3 = new L.geoJson(json_HealthFacilities_3, {
            attribution: '',
            interactive: true,
            dataVar: 'json_HealthFacilities_3',
            layerName: 'layer_HealthFacilities_3',
            pane: 'pane_HealthFacilities_3',
            onEachFeature: pop_HealthFacilities_3,
            pointToLayer: function (feature, latlng) {
                var context = {
                    feature: feature,
                    variables: {}
                };
                return L.marker(latlng, style_HealthFacilities_3_0(feature));
            },
        });
        bounds_group.addLayer(layer_HealthFacilities_3);
        map.addLayer(layer_HealthFacilities_3);
        function pop_ProminantFeatures_4(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['id'] !== null ? autolinker.link(feature.properties['id'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['Prominant'] !== null ? autolinker.link(feature.properties['Prominant'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_ProminantFeatures_4_0() {
            return {
                pane: 'pane_ProminantFeatures_4',
        rotationAngle: 0.0,
        rotationOrigin: 'center center',
        icon: L.icon({
            iconUrl: 'markers/amenity=police.svg',
            iconSize: [17.479999999999997, 17.479999999999997]
        }),
                interactive: true,
            }
        }
        map.createPane('pane_ProminantFeatures_4');
        map.getPane('pane_ProminantFeatures_4').style.zIndex = 404;
        map.getPane('pane_ProminantFeatures_4').style['mix-blend-mode'] = 'normal';
        var layer_ProminantFeatures_4 = new L.geoJson(json_ProminantFeatures_4, {
            attribution: '',
            interactive: true,
            dataVar: 'json_ProminantFeatures_4',
            layerName: 'layer_ProminantFeatures_4',
            pane: 'pane_ProminantFeatures_4',
            onEachFeature: pop_ProminantFeatures_4,
            pointToLayer: function (feature, latlng) {
                var context = {
                    feature: feature,
                    variables: {}
                };
                return L.marker(latlng, style_ProminantFeatures_4_0(feature));
            },
        });
        bounds_group.addLayer(layer_ProminantFeatures_4);
        map.addLayer(layer_ProminantFeatures_4);
        function pop_BOUNDRY_5(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['id'] !== null ? autolinker.link(feature.properties['id'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['BOUNDRY'] !== null ? autolinker.link(feature.properties['BOUNDRY'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_BOUNDRY_5_0() {
            return {
                pane: 'pane_BOUNDRY_5',
                opacity: 1,
                color: 'rgba(219,30,42,1.0)',
                dashArray: '',
                lineCap: 'square',
                lineJoin: 'bevel',
                weight: 3.0,
                fillOpacity: 0,
                interactive: true,
            }
        }
        map.createPane('pane_BOUNDRY_5');
        map.getPane('pane_BOUNDRY_5').style.zIndex = 405;
        map.getPane('pane_BOUNDRY_5').style['mix-blend-mode'] = 'normal';
        var layer_BOUNDRY_5 = new L.geoJson(json_BOUNDRY_5, {
            attribution: '',
            interactive: true,
            dataVar: 'json_BOUNDRY_5',
            layerName: 'layer_BOUNDRY_5',
            pane: 'pane_BOUNDRY_5',
            onEachFeature: pop_BOUNDRY_5,
            style: style_BOUNDRY_5_0,
        });
        bounds_group.addLayer(layer_BOUNDRY_5);
        map.addLayer(layer_BOUNDRY_5);
        function pop_MajorRoad_6(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <th scope="row">id</th>\
                        <td>' + (feature.properties['id'] !== null ? autolinker.link(feature.properties['id'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['Major Road'] !== null ? autolinker.link(feature.properties['Major Road'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_MajorRoad_6_0() {
            return {
                pane: 'pane_MajorRoad_6',
                opacity: 1,
                color: 'rgba(72,123,182,1.0)',
                dashArray: '',
                lineCap: 'square',
                lineJoin: 'bevel',
                weight: 3.0,
                fillOpacity: 0,
                interactive: true,
            }
        }
        map.createPane('pane_MajorRoad_6');
        map.getPane('pane_MajorRoad_6').style.zIndex = 406;
        map.getPane('pane_MajorRoad_6').style['mix-blend-mode'] = 'normal';
        var layer_MajorRoad_6 = new L.geoJson(json_MajorRoad_6, {
            attribution: '',
            interactive: true,
            dataVar: 'json_MajorRoad_6',
            layerName: 'layer_MajorRoad_6',
            pane: 'pane_MajorRoad_6',
            onEachFeature: pop_MajorRoad_6,
            style: style_MajorRoad_6_0,
        });
        bounds_group.addLayer(layer_MajorRoad_6);
        map.addLayer(layer_MajorRoad_6);
        var osmGeocoder = new L.Control.Geocoder({
            collapsed: true,
            position: 'topleft',
            text: 'Search',
            title: 'Testing'
        }).addTo(map);
        document.getElementsByClassName('leaflet-control-geocoder-icon')[0]
        .className += ' fa fa-search';
        document.getElementsByClassName('leaflet-control-geocoder-icon')[0]
        .title += 'Search for a place';
        var baseMaps = {};
        L.control.layers(baseMaps,{'<img src="legend/MajorRoad_6.png" /> Major Road': layer_MajorRoad_6,'<img src="legend/BOUNDRY_5.png" /> BOUNDRY': layer_BOUNDRY_5,'<img src="legend/ProminantFeatures_4.png" /> Prominant Features': layer_ProminantFeatures_4,'<img src="legend/HealthFacilities_3.png" /> Health Facilities': layer_HealthFacilities_3,'<img src="legend/ReligiosStructures_2.png" /> Religios Structures': layer_ReligiosStructures_2,'<img src="legend/MinorRoad_1.png" /> Minor Road': layer_MinorRoad_1,'<img src="legend/AcadamicsFacilities_0.png" /> Acadamics Facilities': layer_AcadamicsFacilities_0,}).addTo(map);
        setBounds();
        var i = 0;
        layer_MinorRoad_1.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['ROAD'] !== null?String('<div style="color: #000000; font-size: 10pt; font-family: \'MS Shell Dlg 2\', sans-serif;">' + layer.feature.properties['ROAD']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_MinorRoad_1'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        var i = 0;
        layer_HealthFacilities_3.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['id'] !== null?String('<div style="color: #000000; font-size: 10pt; font-family: \'MS Shell Dlg 2\', sans-serif;">' + layer.feature.properties['id']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_HealthFacilities_3'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        var i = 0;
        layer_ProminantFeatures_4.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['Prominant'] !== null?String('<div style="color: #000000; font-size: 10pt; font-family: \'MS Shell Dlg 2\', sans-serif;">' + layer.feature.properties['Prominant']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_ProminantFeatures_4'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        var i = 0;
        layer_MajorRoad_6.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['Major Road'] !== null?String('<div style="color: #000000; font-size: 9pt; font-family: \'MS Shell Dlg 2\', sans-serif;">' + layer.feature.properties['Major Road']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_MajorRoad_6'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        map.addControl(new L.Control.Search({
            layer: layer_MinorRoad_1,
            initial: false,
            hideMarkerOnCollapse: true,
            propertyName: 'id'}));
        document.getElementsByClassName('search-button')[0].className +=
         ' fa fa-binoculars';
        resetLabels([layer_MinorRoad_1,layer_HealthFacilities_3,layer_ProminantFeatures_4,layer_MajorRoad_6]);
        map.on("zoomend", function(){
            resetLabels([layer_MinorRoad_1,layer_HealthFacilities_3,layer_ProminantFeatures_4,layer_MajorRoad_6]);
        });
        map.on("layeradd", function(){
            resetLabels([layer_MinorRoad_1,layer_HealthFacilities_3,layer_ProminantFeatures_4,layer_MajorRoad_6]);
        });
        map.on("layerremove", function(){
            resetLabels([layer_MinorRoad_1,layer_HealthFacilities_3,layer_ProminantFeatures_4,layer_MajorRoad_6]);
        });
        </script>
    </body>
</html>
