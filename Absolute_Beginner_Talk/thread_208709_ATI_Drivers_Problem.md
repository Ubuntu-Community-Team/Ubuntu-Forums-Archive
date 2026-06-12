---
title: "ATI Drivers Problem"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by white on 2006-07-04
I have tried nearly every How-To in the Tips & Tricks subforum to installing and getting my x800 pro AGP to show up with fglrxinfo. This mesa3d driver is literally driving me insane. I have installed fglrx xorg drivers, uninstalled them, changed the conf, blacklisted fglrx, clean installed Ubuntu, started over after said reinstall and I still can not get rid of the mesa3d problem. Glxgears still gives me a rock solid WHOPPING 40 fps, still.

Here's my .conf (the important parts)
```
Section "Monitor"
	Identifier   "PF775b"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
	Monitor    "PF775b"
	DefaultDepth     24
	SubSection "Display"
```
```
Section "DRI"
	Mode         0666
EndSection
```

The fglrxinfo.
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

What am I to do? :| I'd really like to try XGL and compiz but I can't do a thing until this is fixed.

---

### Post by MaximB on 2006-07-04
I've asked this question and got help...search for my question about ati video card...(it's almost exact problem).

---

### Post by adam.tropics on 2006-07-04
I am sure you have been here already, but just in case, [this works for me]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") every time....except this last week, with the latest ones from ATI, the method there, using the ones from repos still works for me though.

---

### Post by white on 2006-07-04
I have finally got it working, after many attempts I have slain my mesa3d overlords.

It seems all I needed was to reconfigure x after uninstalling fglrx, use vesa, reinstall the restricted modules, and then fglrx again.

The funny thing is, I've done this **EXACT** thing before yielding no results.

---

### Post by adam.tropics on 2006-07-04
> The funny thing is, I've done this EXACT thing before yielding no results.

It can get like that at times! I can't tell ya how many times I said the exact same thing when first starting out trying to get the ATI stuff working. After a few goes it gets fairly straightforward. Don't believe me, uninstall it all and try again!!! Go on, I dare ya! Just kidding. Glad it's working now for you.

Your next challenge can be found [here.]("http://www.compiz.net/viewtopic.php?id=389"). Method 2 is my preferance, but they are both pretty good....

---

### Post by MaximB on 2006-07-04
it remind me of MS windows...that's very bad...
I think it's GUI problems

---

