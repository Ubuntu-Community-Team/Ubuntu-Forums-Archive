---
title: "Trackpad discussion"
date: 2007-06-17
forum: Apple Intel Users
---

### Post by NickFury on 2007-06-17
Well, I fineally got Feisty on my  Macbook Pro C2D, I have wireless, beryl, backlikght, keyboard backlight etc all working great.  However, the trackpad right now is leaving alot to be desired.  Right now my biggest complaint about it is how the trackpad will just just become 'unresponsive' and I will really have to my finger around the trackpad to get it going again.  I would really love to have almost the same trackpad response I get in OS-X!  That would be perfect :)

I was hoping that people who have their trackpad working good could post up their xorg.conf for the rest of us to use.

Here is mine, it still leaves a little to be desired.
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents" "true"
        #Option          "Device"                "/dev/psaux"
        #Option          "Protocol"              "auto-dev"
        #Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
	#Option		"CorePointer"
	Option		"Device"	"/dev/input/mouse0"
	Option		"Protocol"	"auto-dev"
	Option		"LeftEdge"	"100"
	Option		"RightEdge"	"1100"
	Option		"TopEdge"	"50"
	Option		"BottomEdge"	"300"
	Option		"FingerLow"	"20"
	Option		"FingerHigh"	"30"
	Option		"MaxTapTime"	"150"
	Option		"MaxTapMove"	"90"
	Option		"MaxDoubleTapTime"	"180"
	Option		"VertScrollDelta"	"25"
	Option		"HorizScrollDelta"	"30"
	Option		"VertTwoFingerScroll"	"true"
	#Option		"HorizTwoFingerScroll"	"true"
	Option		"FastTaps"	"true"
	#Option		"TapButton2"	"3"
	Option		"TapButton3"	"2"
	Option		"MinSpeed"	"0.5"
	Option		"MaxSpeed"	"3.5"
	Option		"AccelFactor"	"0.40"
	#Option		"SHMConfig"	"on"
EndSection


```

---

