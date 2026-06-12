---
title: "Vertical Scrolling w/ Toshiba 5105-S501"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by zephyrus54 on 2006-12-11
I've searched the forums for methods of enabling vertical scrolling, but none have them have worked for my laptop.  I'm using a Toshiba Satellite 5105-S501, so if anyone out there has gotten their synaptics touchpad to vertically scroll on this laptop or a similar model please let me know.  Thanks.

---

### Post by doctorbighands on 2007-08-23
I'm having an identical issue with my ALPS (also synaptics? I think so) touchpad on my HP machine. I want vertical scroll back!!

Help?

EDIT:

I thought I'd post the relevant section of my xorg file. Maybe that will tip someone off.

```


Section "InputDevice"
	Identifier	"ALPS"
	Driver		"synaptics"
	Option		"AlwaysCore"
	Option		"Device"		"/dev/input/event3"
	Option		"Protocol"		"event"
	Option		"LeftEdge"		"120"
	Option		"RightEdge"		"830"
	Option		"TopEdge"		"120"
	Option		"BottomEdge"		"650"
	Option		"FingerLow"		"14"
	Option		"FingerHigh"		"15"
	Option		"MaxTapTime"		"180"
	Option		"MaxTapMove"		"110"
	Option		"ClickTime"		"0"
	Option		"EmulateMidButtonTime"	"75"
	Option		"VertScrollDelta"	"10"
	Option		"HorizScrollDelta"	"0"
	Option		"MinSpeed"		"0.8"
	Option		"MaxSpeed"		"5"		
	Option		"AccelFactor"		"0.020"
	Option		"EdgeMotionMinSpeed"	"200"
	Option		"EdgeMotionMaxSpeed"	"200"
	Option		"UpDownScrolling"	"0"
	Option		"CircularScrolling"	"0"
	Option		"CircScrollDelta"	"0.1"
	Option		"CircScrollTrigger"	"2"
	Option		"SHMConfig"		"true"
	Option		"TouchpadOff"		"2"
EndSection


```

---

### Post by anewguy on 2007-08-24
I have a Gateway laptop (cheap) with a Synaptics touchpad and I have both scrolls working.  So, I have a question:

Did you try gsynaptics package prior to all that stuff in you conf file?

Here's all that's in my conf file for the touchpad:


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
EndSection


Then go to the synaptics package manager (system/administration/Synaptics Package Manager).  Search for the string "gsynaptics", click the box and say you want to install, then just click the apply button.

When all of that has finished, log off, then at the log on screen hold down ctrl alt and press the backspace key, then release all of the keys.  This will restart the X server to make use of the modified conf file.  Now just log on and go to System/Preferences/Touchpad.  In the various tabs there you can set your scrolling, turn tapping off/on, etc.

:)

---

### Post by doctorbighands on 2007-08-25
> **anewguy said:**
> Then go to the synaptics package manager (system/administration/Synaptics Package Manager).  Search for the string "gsynaptics", click the box and say you want to install, then just click the apply button.

THANK YOU for this!! I got my touchpad figured out and configured just like I like it, finally!!! Also, this helped me to learn what Synaptics is. I had seen it mentioned elsewhere in the forums, but I wasn't sure what it was.

Very helpful, as usual. Thank you!

---

### Post by Kivrin on 2007-09-20
I tried gynaptics, but it keeps saying that my SHMConfig must be set to true in the xorg.conf file. However, SHMConfig IS set to "true". I tried it with "on" also, to no effect. Augh.

---

### Post by anewguy on 2007-10-21
> **Kivrin said:**
> I tried gynaptics, but it keeps saying that my SHMConfig must be set to true in the xorg.conf file. However, SHMConfig IS set to "true". I tried it with "on" also, to no effect. Augh.

did you double check your spelling - especially the quotes and capital letters?  I would have thought that would work, but maybe there is something different with your PC.

---

### Post by rasmusbp on 2007-11-25
I have the same problem - can't get the vertical scrolling working in Ubuntu 7.10. I'm on a asus m6n - scrolling works just fine in XP. I've followed the instructions carefully reg the conf file, gsynaptics has been installed and seems to be working, but scrolling just doesn't. here the relevant output from my xorg.conf: 

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "SHMConfig" "true"
Option "RightEdge" "5900"
Option "VertEdgeScroll" "true"
EndSection

Can someone please help?

Thanks!  : )
Rasmus

---

### Post by homeriq5 on 2008-04-27
apparently altering the touchapd device section isnt enought to get vertical scrolling or gsynaptics to work. I was having the same problem on my old sony, and I ended following this guy's directions and it solved my problem:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/173411/comments/17](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/173411/comments/17)

basically you add a few lines to the modules, serverlayout, and touchpad sections of your xorg.conf file and you're good to go after a reboot.  Hope this helps!

---

