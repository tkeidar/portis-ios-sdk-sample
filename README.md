# portis-ios-sdk-sample

This sample code is a POC for the portis iOS SDK.
1. It's a native swift app which opens a webview of html page (/html/portis.html), this page contains only the portis integration, so currently, the user can login and view the portis widget.
1. This POC demonstrates also the 2-way communication between the Portis SDK and a native iOS app.
1. The ViewController.swift file contains the implementation of `userContentController` which accepts messages on the native app from the Portis SDK with the code below:
```
try {
      console.log('Sending message from SDK to SWIFT');
      (window as any).webkit.messageHandlers.callbackHandler.postMessage({
        from: 'Tom',
        content: 'Hello from JavaScript',
      });
    } catch (err) {
      console.log('The native context does not exist yet');
    }
```

on the other end, the native app can also send messages to the JS code using:
```
let js = "nativeMessage('hi there!');"
webView.evaluateJavaScript(js, completionHandler: nil)
```
(`nativeMessage` function is available under /html/portis.html)
