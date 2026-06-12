---
title: "Disable scroll on trackpad?"
date: 2007-07-02
forum: Apple Intel Users
---

### Post by grim1234 on 2007-07-02
I catch the right edge of the trackpad quite often when typing, resulting in me typing in some other part of the document. 

Is it possible to disable the scroll?

Or, to make it like osx, with two fingers on the pad meaning scroll instead of the right hand side?

---

### Post by kerry_s on 2007-07-02
add> syndaemon -d
to your session startup and when you type your touchpad will be disabled till 1 sec after you finish typing

---

### Post by ronocdh on 2007-07-02
There are many posts in this forum mentioning Gsynaptic or Qsynaptics. These will allow you to configure your trackpad a bit, although I've never gotten two-finger scrolling to work in Ubuntu how it does in OS X; it's the feature I miss most! Reading this forums is brutal without it, unless I'm at a desk with a mouse, of course.

---

### Post by grim1234 on 2007-07-02
I found a config that enables two finger scroll, it works, but not quite as well as on osx.

> Section "InputDevice"
	Identifier	"MacBook Touchpad"
	Driver		"synaptics"
	Option 		"SHMConfig" "on"
	Option		"CorePointer"
	Option		"SendCoreEvents" "true"
	Option		"Device" "/dev/psaux"
	Option 		"Protocol" "auto-dev"
	Option 		"LeftEdge" "100"
	Option 		"RightEdge" "1120"
	Option 		"TopEdge" "50"
	Option 		"BottomEdge" "310"
	Option 		"FingerLow" "20"
	Option 		"FingerHigh" "30"
	Option 		"MaxTapTime" "150"
	Option 		"MaxTapMove" "220"
	Option 		"MaxDoubleTapTime" "180"
	Option 		"VertScrollDelta" "25"
	Option 		"VertTwoFingerScroll" "true"
	Option 		"TapButton2" "3"
	Option 		"TapButton3" "2"
	Option 		"MinSpeed" "0.79"
	Option 		"MaxSpeed" "0.88"
	Option 		"AccelFactor" "0.015"
EndSection

---

### Post by thully on 2007-07-02
This might work better - it seems like the best that can be done in Ubuntu.
Scrolling is with two fingers, tapping the left corner does a right click, and tapping the right corner does a middle click.  Fiddle with the settings (especially the speed/acceleration) as you wish...

Section "InputDevice"
       Identifier   "Synaptics Touchpad"
       Driver   "synaptics"
       Option  "SendCoreEvents"        "true"
       Option  "Device"        "/dev/psaux"
       Option  "Protocol"      "auto-dev"
       Option  "LeftEdge"      "150"
       Option  "RightEdge"     "1070"
       Option  "TopEdge"       "100"
       Option  "BottomEdge"    "310"
       Option  "FingerLow"     "25"
       Option  "FingerHigh"    "30"
       Option  "MaxTapTime"    "180"
       Option  "MaxTapMove"    "220"
       Option  "MaxDoubleTapTime"      "180"
       Option  "HorizEdgeScroll" "0"
       Option  "VertEdgeScroll" "0"
       Option  "TapButton1"            "0"
       Option  "TapButton2"            "0"
       Option  "TapButton3"            "0"
       Option  "LockedDrags"           "off"
       Option  "VertScrollDelta"       "20"
       Option  "HorizScrollDelta"      "50"
       Option  "VertTwoFingerScroll"  "1"
       Option  "HorizTwoFingerScroll" "1"
       Option  "MinSpeed"      "1.10"
       Option  "MaxSpeed"      "1.30"
       Option  "AccelFactor"   "0.08"
       Option  "Emulate3Buttons"       "true"
       Option  "SHMConfig"     "on"
# corner buttons
        Option "RTCornerButton" "0"
        Option "RBCornerButton" "2"
        Option "LTCornerButton" "0"
        Option "LBCornerButton" "3"
EndSection

---

### Post by ivesjd on 2007-07-02
Wow, that two-finger scroll actually works good. I even put my fingers verticly and it worked. Nice find.

---

### Post by grim1234 on 2007-07-03
Nice, thanks thully, that works well.

---

### Post by eros82ca on 2007-07-04
Ok, so where do you insert the code?  I'm a little lost.

---

### Post by cyberdork33 on 2007-07-04
It is the trackpad configuration in your xorg.conf

---

### Post by eros82ca on 2007-07-04
Thank you, I should have know that.  For some reason I was thinking you had to manually edit another file or were entering code somewhere else.

Again thank you.

---

### Post by ivesjd on 2007-08-17
I just realised that my horizontal scroll isnt working. I am using the above xorg and was wondering if anyone else has horizontal scroll working with the above settings.

---

### Post by cyberdork33 on 2007-08-17
really just guessing, but I think this has something to do with it:

```
        Option  "HorizEdgeScroll" "0"
       Option  "VertEdgeScroll" "0"
```

---

### Post by ivesjd on 2007-08-17
Oh, I guess I'm not using the same config, but I figured it out anyway, In the touchpad gui config under system, horizontal scroll was disabled even though I had it enabled in the xorg, it didn't work.

---

### Post by cyberdork33 on 2007-08-18
> **ivesjd said:**
> Oh, I guess I'm not using the same config, but I figured it out anyway, In the touchpad gui config under system, horizontal scroll was disabled even though I had it enabled in the xorg, it didn't work.
yea i think that the gsynaptics / qsynaptics or whatever alters the set variables, so if you are using those, it will change what is set in the xorg file.

---

