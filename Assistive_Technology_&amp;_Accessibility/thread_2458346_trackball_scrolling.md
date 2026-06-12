---
title: "trackball scrolling"
date: 2021-02-22
forum: Assistive Technology &amp; Accessibility
---

### Post by slomobile on 2021-02-22
I have a Jetson Nano and small screen on my wheelchair.  I need to scroll a lot to view things like schematics on the necessarily small screen.  I would like to use a [Kensington Orbit trackball]("https://www.kensington.com/p/products/electronic-control-solutions/trackball-products/orbit-trackball-with-scroll-ring/") dedicated to scrolling function.  I would like to use the ring, normally used for scrolling to control zoom, and the buttons on either side to be "Forward" and "Back" browser buttons.  A different pointing device, touchpad or mouse will control normal mouse functions.  How can I accomplish this with Ubuntu 18.04?

I think a microcontroller with USB host capability could be used to scan both HID inputs and only output the appropriate signals to the Ubuntu machine, but that sounds like more work than necessary when Ubuntu can host both HID devices directly.  How is horizontal and vertical scrolling triggered anyway?  I might also like to add foot switches to scroll at some point if hand control becomes erratic.

---

