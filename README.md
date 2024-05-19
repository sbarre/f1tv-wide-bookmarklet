# F1TV Widescreen Bookmarklet

This is a Javascript bookmarklet to make the video player fill the width of the browser window on F1TV.

I'm not sure why they think we want those black bars on the side, or wouldn't want to have the window be the full width, but here we are.

If you know how to install a bookmarklet, go to [https://sbarre.github.com/f1tv-wide-bookmarklet](https://sbarre.github.com/f1tv-wide-bookmarklet) where you can inspect and install the bookmarklet.

### The code

In the spirit of "don't download and install random code from the Internet", here is the source code for the bookmarklet. All it does is inject CSS overrides into the page.

```js
;(function () {
  var css = `#app > div > div.content > main > div:nth-child(1) {
        max-width: 100% !important;
        width: 100% !important;
    }
    @media (min-width: 1200px) {
        .container { max-width: 100% !important; width: 100% !important; }
    }
    @media (min-width: 992px) {
        .container { max-width: 100% !important; width: 100% !important; }
    }
    @media (min-width: 768px) {
        .container { max-width: 100% !important; width: 100% !important; }
    }
    @media (min-width: 576px) {
        .container { max-width: 100% !important; width: 100% !important; }
    }
    .inset-video-item-container.f1-padding { 
        max-width: none !important; padding: 0px !important; 
    }
    #app > div > div.content > main > div:nth-child(1) > div > div > div > div.inset-video-item-image-container.position-relative.d-flex {
        display: block !important;
    }`
  var style = document.createElement("style")
  if (style.styleSheet) {
    style.styleSheet.cssText = css
  } else {
    style.appendChild(document.createTextNode(css))
  }
  document.getElementsByTagName("head")[0].appendChild(style)
})()
```
