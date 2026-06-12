---
title: "Direct Rendering: no. How to get it to YES?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by eooon on 2007-01-29
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect


I have followed this guide  ( [https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html) 3D ATI Video Card Driver ) but no luck.

I got a X1900XTX card. I followed that guide 100% and also checked some other guides.
This is the output from xorg.conf:
Section "Device"
	Identifier	"ATI Graphics Adapter"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"VideoOverlay" "on"
	Option		"UseFBDev"		"true"
EndSection

Im new to linux and i really want to try Beryl, but I find it harder to get the basic things working in Linux then the hardest task in Windows... :(

---

### Post by Denn1s on 2007-01-29
making things work is the fun part ;P 
well, for wath i found in google, ATI released drivers for that card in the 8.24.8 package, ill post u a link when i found one

edit

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.24.8.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.24.8.html)

this page looks promising, you may need to install "alien" to get an rpm workin (i couldnt find were to click and download)

---

### Post by eooon on 2007-01-29
I tried the ATI drivers first and had no luck. After some support from IRC i changed over to the Xorg drivers, and I hope to be able to use those now.

---

