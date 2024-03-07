var dataset = ee.FeatureCollection('FAO/GAUL/2015/level1');

var bgd = dataset.filter(ee.Filter.eq("ADM0_NAME","Bangladesh"))

print(bgd, "bgd_boundary")
var sylhet = bgd.filter(ee.Filter.eq("ADM1_NAME","Sylhet"))
print(sylhet)

print(bgd)
Map.centerObject(bgd)
Map.addLayer(bgd)
var styleParams = {
  fillColor: 'yellow',
  color: 'FFFF00',
  width: 1.0,
};

dataset = bgd.style(styleParams);


Map.addLayer(dataset, {}, 'First Level Administrative Units');
Map.addLayer(sylhet.style(styleParams),{},"sylhet")
