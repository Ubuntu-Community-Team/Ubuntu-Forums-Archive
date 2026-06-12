---
title: "Custom mouse configuration in xorg.conf"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-11-21
I may be way off base here, but I was wondering about configuration of the mouse buttons in xorg.conf. If ZAxisMapping controls the up and down scroll, would XAxisMapping entry control the side to side scroll? I have a Logitech Laser mouse with 9 buttons. 4 & 5 are ZAxisMapping in xorg.conf and 8 & 9 are the side to side controls on the mouse, but they don't work. Just wondering if an XAxisMapping "8 9" entry under the ZAxisMapping "4 5" would do anything to the horizontal scroll buttons ?  The 6 & 7 buttons are forward and back for my browser and the work fine. Any thoughts --------

---

### Post by jerrynewt on 2007-11-22
bump

---

### Post by jerrynewt on 2007-11-23
Any ideas on this at all ??

---

### Post by jerrynewt on 2007-11-24
One more time. As I remember from shcool (back in ancient times), in plotting x,y, and z -- if Zaxis is the vertical, then either x or y should be the horizontal, or maybe I have just fallen and hit my head one too many times. Anyone have any suggestions on this ??

---

### Post by LowSky on 2007-11-24
```
Section "InputDevice"
	Identifier	"Logitech USB Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
	Option          "ButtonMapping"         "1 2 3 6 7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection
```

that how i set up my mouse
but i dont have verticle scroll, why not try adding a "XAxisMapping" "# #"

---

### Post by jerrynewt on 2007-11-24
Well LowSky, I tried the XAxis thing and rebooted to a blank screen. Had to copy the original xorg.conf back over before I could get my desktop back, so guess I will have to do without the horizontal scroll buttons working for now. It was worth a try and only took bout three minutes to fix. Thanks again and "Happy Holidays"

---

