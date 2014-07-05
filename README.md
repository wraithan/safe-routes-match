# safe-routes-match

A simple module to 404 when there isn't a match for a route.

## usage

From your initial request handler:

``` JavaScript
var http = require('http')
var url = require('url')
var safe_match = require('safe-routes-match')
var router = require('./lib/router')

http.createServer(function (req, res) {
  var path = url.parse(req.url).pathname
  var match = router.match(path)
  safe_match(req, res, match)
})
```

If you are doing the `.next()` thing:

``` JavaScript
function myRoute (req, res, match) {
  // Do interesting middleware-y stuff
  match = match.next()
  safe_match(req, res, match)
}
```