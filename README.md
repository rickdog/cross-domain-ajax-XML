# cross-domain-ajax-XML
XML Cross-domain AJAX

https://codio.com/p/create/?from_github=rickdog/cross-domain-ajax-XML

Fixes Padolsey's jJQuery.ajax override for executing cross-domain Ajax (XSS).
post: http://james.padolsey.com/javascript/cross-domain-requests-with-jquery/
source: https://github.com/padolsey-archive/jquery.fn/tree/master/cross-domain-ajax

All based on Heilmann's original post: http://christianheilmann.com/2010/01/10/loading-external-content-with-ajax-using-jquery-and-yql/

This version fixes a problem with Padolsey's function - it fails when getting raw XML.

I've wrapped the jQuery.ajax override in a function that supports a callback and also jQuery promise.

Callback:
```
getXML("http://feeds.feedburner.com/leaverou",
  function(response)
  {
  	console.log(response.responseText);
  }
)
```
or promise (or combine if you wish)
```
getXML("http://feeds.feedburner.com/leaverou")
.success(function(response, statusText, xhrObj) {
  console.log(response, statusText, xhrObj);
  if (response.results.length == 1)
  {
  	console.log(response.results[0]);
  }
})
.error(function(xhrObj, textStatus, err) {
  console.log(xhrObj, textStatus, err);
});
```
