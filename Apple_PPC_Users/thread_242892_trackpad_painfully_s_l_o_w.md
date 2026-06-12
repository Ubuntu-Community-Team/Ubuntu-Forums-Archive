---
title: "trackpad painfully s l o w"
date: 2006-08-24
forum: Apple PPC Users
---

### Post by jdwaters on 2006-08-24
I'm running 6.06 from a CD on a Mac Powerbook.
I went to the System menu and selected the Mouse prefs and adjusted my Motion speed to the fastest.
but my trackpad is STILL painfully slow.

is there a separate setting for my trackpad?
how can I fix this?

it's really bad. takes like 8 swipes to get from one side of the screen to the other.

---

### Post by smbrow14 on 2006-08-24
You need to edit your /etc/X11/xorg.conf file. You'll see the Section "InputDevice" and Identifier "Synaptics Touchpad." These are the settings I use (got them from another post on this forum). You can adjust them to suit your preferences:

```

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
# Option "Device" "/dev/input/mice"
Option "Device" "/dev/input/appletouch"
Option "Protocol" "auto-dev"
Option "LeftEdge" "50"
Option "RightEdge" "900" # max 950
Option "TopEdge" "30"
Option "BottomEdge" "304" # max 334
Option "FingerLow" "15"
Option "FingerHigh" "20"
Option "MaxTapTime" "180"
Option "MaxTapMove" "100"
Option "MaxDoubleTapTime" "180"
Option "ClickTime" "100"
Option "FastTaps" "0"
Option "VertScrollDelta" "30"
Option "HorizScrollDelta" "30"
Option "EdgeMotionMinZ" "30"
Option "EdgeMotionMaxZ" "160"
Option "EdgeMotionMinSpeed" "1"
Option "EdgeMotionMaxSpeed" "400"
Option "EdgeMotionUseAlways" "false"
Option "MinSpeed" "0.5"
Option "MaxSpeed" "2.0"
Option "AccelFactor" "0.06"
Option "LockedDrags" "false"
# Option "RTCornerButton" "0"
# Option "RBCornerButton" "0"
Option "LTCornerButton" "0"
Option "LBCornerButton" "0"
Option "TapButton1" "1"
Option "TapButton2" "2"
Option "TapButton3" "3"
Option "CircularScrolling" "1"
Option "CircScrollDelta" "0.1"
Option "CircScrollTrigger" "1"
Option "PalmDetect" "false" # not supported
Option "CoastingSpeed" "1"
Option "SHMConfig" "on"
EndSection

```

---

### Post by jdwaters on 2006-08-25
Is this file on my Live/boot CD?
or already on my Mac?
and if it's already on my Mac, am I going to screw it up for when I'm using MacOSX? which is most of the time.

---

### Post by smbrow14 on 2006-08-25
xorg.conf is the configuration file for xorg, which has nothing at all to do with Mac OS (so yes, it came from the live cd). Editing this file will not affect your trackpad settings in OS X whatsoever. I dual boot between Ubuntu 6.06 and OS X 10.4.x regularly and have had no problems with one's settings affecting the others.

---

