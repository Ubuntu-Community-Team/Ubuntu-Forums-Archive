---
title: "Can't enable tapping on trackpad!"
date: 2008-05-23
forum: Apple Hardware Users
---

### Post by pepperjack on 2008-05-23
Hi
I've been trying to get tapping enabled on my Ubuntu 8.04 install onto a MacBook. I've edited my xorg.conf, and installed gsynaptics, and even added this line to /etc/modprobe.d/options:

install usbhid /sbin/modprobe appletouch && sleep 2 && /sbin/modprobe --ignore-install usbhid $CMDLINE_OPTS

Even though I haven't got a clue what it's doing. Anyway, nothing seems to work, my main priority is getting middle click working so that I can select and paste text easily!

Thanks heaps for any ideas anyone might have. My xorg.conf is below for those interested:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"		"true"
	Option          "LeftEdge" 	     	"100"
	Option          "RightEdge"     	"1100"
	Option          "TopEdge"      		"50"
	Option          "BottomEdge"    	"300"

	Option          "FingerLow"     	"25"
	Option          "FingerHigh"    	"30"
	Option		"MaxTapTime"		"180"
	Option          "MaxTapMove"    	"220"
	Option		"SingleTapTimeout"	"100"
	Option		"MaxDoubleTapTime"	"180"
	Option		"LockedDrags"		"off"

	Option          "TapButton1"    	"0"
	Option          "TapButton2"    	"0"
	Option          "TapButton3"    	"0"
	Option		"RTCornerButton"	"0"
	Option		"RBCornerButton"	"2"
	Option		"LTCornerButton"	"0"
	Option		"LBCornerButton"	"3"

	Option          "MinSpeed"      	"0.70"
	Option          "MaxSpeed"      	"0.90"
	Option          "AccelFactor"   	"0.05"
	Option		"HorizEdgeScroll"	"0"
	Option		"VertEdgeScroll"	"0"
	Option          "VertScrollDelta"       "25"
	Option          "HorizScrollDelta"      "30"
	Option		"VertTwoFingerScroll"	"1"
	Option		"HorizTwoFingerScroll"	"1"
EndSection



Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by volanin on 2008-05-23
```
Option "TapButton1" "0"
Option "TapButton2" "0"
Option "TapButton3" "0"
```

Set these to "1".
:)

---

### Post by cyberdork33 on 2008-05-23
> **volanin said:**
> ```
Option "TapButton1" "0"
Option "TapButton2" "0"
Option "TapButton3" "0"
```Set these to "1".
:)Well, actually, if you are also trying to get middle click working, you need to set one of them to "2".

The man page for synaptics has a description for each of the options. You should only use the specific ones that you want/need.
[http://linux.die.net/man/5/synaptics](http://linux.die.net/man/5/synaptics)

---

### Post by pepperjack on 2008-05-23
Thanks! That's solved it - didn't realise I needed both the TapButtons and the CornerButtons switched on.
Cheers :-)

---

