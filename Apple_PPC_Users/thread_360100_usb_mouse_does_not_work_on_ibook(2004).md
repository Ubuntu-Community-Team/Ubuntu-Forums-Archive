---
title: "usb mouse does not work on ibook(2004)"
date: 2007-02-12
forum: Apple PPC Users
---

### Post by seebol on 2007-02-12
Hi, I installed edgy on my ibook g4 last week. Besides the unsavory options for flash, java, and video in general, I like the experience so far. I still prefer MacOSX, but I really am impressed with how Linux has progressed since I last dabbled in it.

One problem I discovered tonight was that my usb mouse does not work! Well, it can left click, right click, and scroll, but it can't move the cursor (the mouse works on MacOSX). I found a thread [http://ubuntuforums.org/showthread.php?t=348115](http://ubuntuforums.org/showthread.php?t=348115) that said that since I have a synaptics touchpad, I have to alter my xorg.conf file. Well I followed the instructions, and I got an error upon restarting X where the touchpad could not be found.

(EE) Synaptics Mouse no synaptics touchpad detected and no repeater device
(EE) Synaptics Mouse Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Mouse"

And X failed to load. I played around with xorg.conf for a bit, rearranging lines here and there--miraculously, the mouse started working! But it was very very laggy, and as I've lost and forgotten that configuration now.

I'm posting here, because I suspect this may be another "linux on ppc"-specific problem, just like how my ibook can't run qsynaptics, even though scroll functionality works with a third-party driver (iscroll2) under Mac. I am also running pbbuttonsd and powerprefs. Any suggestions? Below is the relevant xorg.conf code I have now. Thanks!

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
	Option		"SHMConfig"		"on"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

```

---

