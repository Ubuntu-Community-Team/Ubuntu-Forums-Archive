---
title: "Touchpad middle click does not work on macbook"
date: 2008-06-25
forum: Apple Hardware Users
---

### Post by flaggh on 2008-06-25
I have a MacBook 2,1 with Hardy 64 installed.  After initially tweaking my xorg file, my middle click would work when I tapped three fingers on the touchpad.  This is no longer working and I have no idea why.

xorg.conf:```

Section "Module"
        Load 		"synaptics"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"mac"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"

  	Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
	
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1"
        Option          "HorizScrollDelta"      "100"
        Option          "VertScrollDelta"       "20"
        Option          "PressureMotionMinZ"    "10"
        Option          "FingerLow"             "10"
        Option          "FingerHigh"            "20"
        Option          "LeftEdge"              "20"
        Option          "RightEdge"             "1200"
        Option          "TopEdge"               "20"
        Option          "BottomEdge"            "370"
        Option          "MinSpeed"            	"0.8"
        Option          "MaxSpeed"              "1.2"
        Option          "AccelFactor"           "0.10"
        Option          "MaxTapMove"            "100"
        Option          "MaxTapTime"            "100"
	Option		"MaxDoubleTapTime"	"200"
        Option          "TapButton2"            "3"
        Option          "TapButton3"            "2"
	#Option		"TapButton1"		"0"
        Option          "SHMConfig"             "on"
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by kosumi68 on 2008-06-25
You are talking about simulating a middle click by holding two fingers on the trackpad and clicking the button, right?

I think it depends on what version of synaptics you are using (I am using 0.14.7~git20070706-mactel1), but in addition to your configuration, I use the following line:

```

        # simulate right button
        Option		"MultiFingerButton"	"1"

```

---

### Post by flaggh on 2008-06-25
No.  Actually I'm talking about tapping three fingers to emulate a middle click which is defined by:
```
Option          "TapButton2"            "3"
```
After viewing the output of synclient, I can see that it is definitely detecting the three finger tap.  Further investigating has also proved that I can even copy and paste by tapping with three fingers.  I cannot however tap and drag using this method.  Could some other program such as pommed be interfering with my xorg configuration?

---

### Post by macvr on 2008-09-03
> **flaggh said:**
>   I cannot however tap and drag using this method.  Could some other program such as pommed be interfering with my xorg configuration?

hi, i'm new to ubuntu...
how to view synclient, my click lock also doesnt work..
have u found a solution?

---

### Post by flaggh on 2008-09-03
Don't know what I was doing wrong but its working now.  To click lock I do a tap (single, double, or triple) followed by a single tap.

---

### Post by macvr on 2008-09-03
> **flaggh said:**
> Don't know what I was doing wrong but its working now.  To click lock I do a tap (single, double, or triple) followed by a single tap.
i'm not using a mac...
should i use all the settings u have set in ur Xorg?

even if i have gsynaptics installed[isnt this just a GUI for the above settings?]?

ps: my click lock works only till i keep my finger on the touchpad, once i release it the item drops!
when i was using XP it just holds till i click to release

[couldnt we ask SYNAPTIC for their touchpad enhancements for linux?]

---

### Post by flaggh on 2008-09-03
I don't think you will want to copy all my settings.  You should just copy the ones you want and adapt them to your touchpad.

My click lock only works as long as I keep my finger on the touchpad too.

---

### Post by macvr on 2008-09-03
> **flaggh said:**
> I don't think you will want to copy all my settings.  You should just copy the ones you want and adapt them to your touchpad.
but are those features same as the ones offered in gsynaptics GUI?

> **flaggh said:**
> My click lock only works as long as I keep my finger on the touchpad too.

if thats the case,i think its a bug
 pls join my bug report:[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/259289]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/259289")
and add ur config

---

### Post by cyberdork33 on 2008-09-03
> **macvr said:**
> if thats the case,i think its a bug
 pls join my bug report:[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/259289](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/259289)
and add ur config
No that is not a bug, that is how it is supposed to work. I think there is another option to actually make it "lock" so you can take your fingers off the pad. 

'man synaptics' is your friend

HINT: Option LockedDrags

---

### Post by macvr on 2008-09-03
> **cyberdork33 said:**
> No that is not a bug, that is how it is supposed to work. I think there is another option to actually make it "lock" so you can take your fingers off the pad. 

'man synaptics' is your friend

HINT: Option LockedDrags
ok , will do... but could u direct me to the directions to use man synaptics? [searchin this forum is giving lot of crap results!]

also i'v been havin these problems with my synaptic, which has been unanswered for ages!!![http://ubuntuforums.org/showthread.php?t=890352]("http://ubuntuforums.org/showthread.php?t=890352")
could ujust check it out and give any suggestions?

EDIT: do i have to remove gsynaptics to use 'man synaptics'?

---

### Post by cyberdork33 on 2008-09-03
> **macvr said:**
> ok , will do... but could u direct me to the directions to use man synaptics? [searchin this forum is giving lot of crap results!]

also i'v been havin these problems with my synaptic, which has been unanswered for ages!!![http://ubuntuforums.org/showthread.php?t=890352](http://ubuntuforums.org/showthread.php?t=890352)
could ujust check it out and give any suggestions?
hehe, you must be very new to linux.

open a terminal, and type 'man synaptics'

This also works for many other things. 
man sudo
man nano

This is how you access the manuals (man is short for manual) on different things on a linux or BSD system.

---

### Post by macvr on 2008-09-03
> **cyberdork33 said:**
> hehe, you must be very new to linux.

yup, no knowledge of linux what so EVER!!!:)
but not tough to get used to...

---

