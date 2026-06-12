---
title: "MacBook Trackpad"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by jadedknight on 2007-12-20
Hey guys & gals, I realize that there are a bunch of posts related to the trackpad and Ubuntu on MacBook's. There is even an entire help section. Yet I would like a few of my own issues addressed if you would be so kind :) So anyways this is currently in my xorg.conf

```
Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "LeftEdge" "10"
Option "RightEdge" "1200"
Option "TopEdge" "10"
Option "BottomEdge" "370"
Option "FingerLow" "10"
Option "FingerHigh" "20"
Option "MaxTapTime" "180"
Option "MaxTapMove" "220"
Option "SingleTapTimeout" "100"
Option "MaxDoubleTapTime" "180"
Option "HorizEdgeScroll" "0"
Option "VertEdgeScroll" "0"
Option "TapButton1" "1"
Option "TapButton2" "3"
Option "TapButton3" "2"
Option "LockedDrags" "off"
Option "VertScrollDelta" "20"
Option "HorizScrollDelta" "50"
Option "VertTwoFingerScroll" "1"
Option "HorizTwoFingerScroll" "1"
Option "MinSpeed" "1.10"
Option "MaxSpeed" "1.30"
Option "AccelFactor" "0.08"
Option "Emulate3Buttons" "true"
Option "SHMConfig" "on"
# corner buttons
Option "RTCornerButton" "0"
Option "RBCornerButton" "0"
Option "LTCornerButton" "0"
Option "LBCornerButton" "0"
EndSection

```

The trackpad feels very buggy, to fast sometimes, to slow, verrrry inaccurate. Also in firefox if I scroll two fingers to the left/right it immitates the back/forward buttons :( Any suggestions?

---

