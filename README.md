# responsive-js

```js

let hasTouchScreen = false;
if ("maxTouchPoints" in navigator) {
  hasTouchScreen = navigator.maxTouchPoints > 0;
} else if ("msMaxTouchPoints" in navigator) {
  hasTouchScreen = navigator.msMaxTouchPoints > 0;
} else {
  const mQ = matchMedia?.("(pointer:coarse)");
  if (mQ?.media === "(pointer:coarse)") {
    hasTouchScreen = !!mQ.matches;
  } else if ("orientation" in window) {
    hasTouchScreen = true; // deprecated, but good fallback
  } else {
    // Only as a last resort, fall back to user agent sniffing
    const UA = navigator.userAgent;
    hasTouchScreen =
      /\b(BlackBerry|webOS|iPhone|IEMobile)\b/i.test(UA) ||
      /\b(Android|Windows Phone|iPad|iPod)\b/i.test(UA);
  }
}

const mediaQuery = window.matchMedia('(min-width: 478px) and (max-width: 767px)')
const desktopClass = document.querySelector(".ipadwrapper")
const mobileClass = document.querySelector(".mobile-comp")
const chromeDesk = /Chrome/i.test(navigator.userAgent)

mediaQuery.addListener(handleDeviceChange)

function handleDeviceChange() {

	if (mediaQuery.matches && hasTouchScreen && !chromeDesk) {
  	console.log("mobile")
  	desktopClass.style.display = "none"
  	mobileClass.style.display = "flex"
	}
}

handleDeviceChange(mediaQuery)

```
