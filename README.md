# api documentation for  [forecast (v0.3.2)](https://ghub.io/forecast)  [![npm package](https://img.shields.io/npm/v/npmdoc-forecast.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-forecast) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-forecast.svg)](https://travis-ci.org/npmdoc/node-npmdoc-forecast)
#### Weather information for node

[![NPM](https://nodei.co/npm/forecast.png?downloads=true)](https://www.npmjs.com/package/forecast)

[![apidoc](https://npmdoc.github.io/node-npmdoc-forecast/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-forecast_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-forecast/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-forecast/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-forecast/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "James Wyse",
        "email": "james@jameswyse.net"
    },
    "bugs": {
        "url": "https://github.com/jameswyse/forecast/issues"
    },
    "dependencies": {
        "moment": "^2.15.1",
        "object-assign": "^4.1.0",
        "request-json": "^0.6.1"
    },
    "description": "Weather information for node",
    "devDependencies": {
        "eslint": "^3.6.1"
    },
    "directories": {},
    "dist": {
        "shasum": "8f0dee77a08b77c822a8fb3a8e8f729a1e2f82b6",
        "tarball": "https://registry.npmjs.org/forecast/-/forecast-0.3.2.tgz"
    },
    "engines": {
        "node": ">= 0.10.0"
    },
    "gitHead": "6e2fabb5a7c573612024abf50cdc81f1793fcb25",
    "homepage": "https://ghub.io/forecast",
    "keywords": [
        "weather",
        "forecast",
        "api",
        "darksky",
        "forecast.io"
    ],
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "jameswyse",
            "email": "james@jameswyse.net"
        }
    ],
    "name": "forecast",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/jameswyse/forecast.git"
    },
    "scripts": {
        "lint": "eslint ."
    },
    "version": "0.3.2"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module forecast](#apidoc.module.forecast)
1.  [function <span class="apidocSignatureSpan">forecast.</span>darksky (options)](#apidoc.element.forecast.darksky)
1.  object <span class="apidocSignatureSpan">forecast.</span>darksky.prototype

#### [module forecast.darksky](#apidoc.module.forecast.darksky)
1.  [function <span class="apidocSignatureSpan">forecast.</span>darksky (options)](#apidoc.element.forecast.darksky.darksky)

#### [module forecast.darksky.prototype](#apidoc.module.forecast.darksky.prototype)
1.  [function <span class="apidocSignatureSpan">forecast.darksky.prototype.</span>get (apiParams, callback)](#apidoc.element.forecast.darksky.prototype.get)
1.  [function <span class="apidocSignatureSpan">forecast.darksky.prototype.</span>query (latlong, callback)](#apidoc.element.forecast.darksky.prototype.query)



# <a name="apidoc.module.forecast"></a>[module forecast](#apidoc.module.forecast)

#### <a name="apidoc.element.forecast.darksky"></a>[function <span class="apidocSignatureSpan">forecast.</span>darksky (options)](#apidoc.element.forecast.darksky)
- description and source-code
```javascript
darksky = function (options) {
  this.options = options || {};
  this.client = new Client('https://api.darksky.net/forecast/' + this.options.key + '/');
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.forecast.darksky"></a>[module forecast.darksky](#apidoc.module.forecast.darksky)

#### <a name="apidoc.element.forecast.darksky.darksky"></a>[function <span class="apidocSignatureSpan">forecast.</span>darksky (options)](#apidoc.element.forecast.darksky.darksky)
- description and source-code
```javascript
darksky = function (options) {
  this.options = options || {};
  this.client = new Client('https://api.darksky.net/forecast/' + this.options.key + '/');
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.forecast.darksky.prototype"></a>[module forecast.darksky.prototype](#apidoc.module.forecast.darksky.prototype)

#### <a name="apidoc.element.forecast.darksky.prototype.get"></a>[function <span class="apidocSignatureSpan">forecast.darksky.prototype.</span>get (apiParams, callback)](#apidoc.element.forecast.darksky.prototype.get)
- description and source-code
```javascript
get = function (apiParams, callback) {
  this.query(apiParams, function (err, res, body) {
    if (err || !body || !body.currently) {
      return callback(err);
    }
    return callback(null, body);
  });
}
```
- example usage
```shell
...
ttl: {            // How long to cache requests. Uses syntax from moment.js: http://momentjs.com/docs/#/durations/creating/
  minutes: 27,
  seconds: 45
}
});

// Retrieve weather information from coordinates (Sydney, Australia)
forecast.get([-33.8683, 151.2086], function(err, weather) {
if(err) return console.dir(err);
console.dir(weather);
});

// Retrieve weather information, ignoring the cache
forecast.get([-33.8683, 151.2086], true, function(err, weather) {
if(err) return console.dir(err);
...
```

#### <a name="apidoc.element.forecast.darksky.prototype.query"></a>[function <span class="apidocSignatureSpan">forecast.darksky.prototype.</span>query (latlong, callback)](#apidoc.element.forecast.darksky.prototype.query)
- description and source-code
```javascript
query = function (latlong, callback) {
  if (!this.options.key) {
    return callback('No API key specified - Get one from https://darksky.net/dev');
  }

  var apiQuery = [];

  if (this.options.units.charAt(0).toLowerCase() === 'c') {
    apiQuery.push('units=si');
  }

  if (this.options.lang) {
    apiQuery.push('lang=' + this.options.lang);
  }

  var params = [
    latlong.join(','),
    apiQuery.join('&')
  ].join('?');

  return this.client.get(params, callback);
}
```
- example usage
```shell
...
    apiQuery.join('&')
  ].join('?');

  return this.client.get(params, callback);
};

DarkSky.prototype.get = function (apiParams, callback) {
  this.query(apiParams, function (err, res, body) {
    if (err || !body || !body.currently) {
      return callback(err);
    }
    return callback(null, body);
  });
};
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
