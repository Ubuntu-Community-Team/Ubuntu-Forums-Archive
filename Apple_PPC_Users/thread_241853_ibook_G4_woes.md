---
title: "ibook G4 woes"
date: 2006-08-22
forum: Apple PPC Users
---

### Post by urmom9388 on 2006-08-22
i have a few problems with my ibook g4. I am dual booting ubuntu and mac fine, but I have a few problems, One problem I have is that ubuntu boots on default rather than mac, how do I change this? My biggest problem of all is that the trackpad in linux is unbearably slow, how can I change this? My last problem is that my airport extreme card will not work. Sorry if these questions have been asked before (I am setting this up for my brothers, I use Fedora).

---

### Post by jdp on 2006-08-23
To fix the boot issue, edit the yaboot.conf file and add the line **defaultos=macosx** to it.  Save, and run **ybin -v** to reconfigure YaBoot with the new setting.  See **man yaboot.conf** for more info.

---

### Post by manatee on 2006-08-23
Hi,

I have an ibook G4 12'' 1,33 Ghz and i had the same problem for my trackpad. I changed my xorg.conf and now it works :

> Section "InputDevice"
	Identifier	"Synaptics Touchpad"      
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

if you want (and if your laptop is the same as mine) you also can have the scroll on your trackpad, just modify your xorg.conf like this :

> Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
#    Option        "Device"        "/dev/input/mice"
    Option        "Device"        "/dev/input/appletouch"
    Option        "Protocol"        "auto-dev"
    Option        "LeftEdge"        "50"
    Option        "RightEdge"       "900"          # max 950
    Option        "TopEdge"        "30"
    Option        "BottomEdge"     "304"          # max 334
    Option        "FingerLow"        "15"
    Option        "FingerHigh"        "20"
    Option        "MaxTapTime"        "180"
    Option        "MaxTapMove"        "100"
    Option        "MaxDoubleTapTime"    "180"
    Option        "ClickTime"        "100"
    Option        "FastTaps"        "0"
    Option        "VertScrollDelta"    "30"
    Option        "HorizScrollDelta"    "30"
    Option        "EdgeMotionMinZ"    "30"
    Option        "EdgeMotionMaxZ"    "160"
    Option        "EdgeMotionMinSpeed"    "1"
    Option        "EdgeMotionMaxSpeed"    "400"
    Option        "EdgeMotionUseAlways"    "false"
    Option        "MinSpeed"        "0.5"
    Option        "MaxSpeed"        "2.0"
    Option        "AccelFactor"        "0.12"
    Option        "LockedDrags"        "false"
   # Option        "RTCornerButton"    "0"
   # Option        "RBCornerButton"    "0"
    Option        "LTCornerButton"    "0"
    Option        "LBCornerButton"    "0"
    Option        "TapButton1"        "1"
    Option        "TapButton2"        "2"
    Option        "TapButton3"        "3"
    Option        "CircularScrolling"    "1"
    Option        "CircScrollDelta"    "0.1"
    Option        "CircScrollTrigger"    "1"
    Option        "PalmDetect"        "false"    # not supported
    Option        "CoastingSpeed"        "1"
    Option        "SHMConfig"        "on"
EndSection

i hope it will help (sorry for my english)

---

### Post by spinz8 on 2006-08-23
Hi manatee,
 Would appreciate it if you can give us the terminal's command to edit xorg.conf file.
Thanks.

---

### Post by stmiller on 2006-08-23
$ sudo nano /etc/X11/xorg.conf

Then Cntl-X, and Y to save.

---

### Post by spinz8 on 2006-08-28
Works like charm :D Perfect!
Thank you manatee and stmiller.

---

