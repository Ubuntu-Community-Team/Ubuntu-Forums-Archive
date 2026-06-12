---
title: "[SOLVED] Two finger scrolling"
date: 2008-04-14
forum: Apple Intel Users
---

### Post by Monsoonx27 on 2008-04-14
I set up two finger scrolling which works fine except when in firefox when causes the pages to go back to the previous pages when used.

How do i stop this

here is my /etc/X11/xorg.conf



Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "true"
        Option          "LeftEdge"              "10"
        Option          "RightEdge"             "1200"
        Option          "TopEdge"               "10"
        Option          "BottomEdge"            "370"
        Option          "FingerLow"             "10"
        Option          "FingerHigh"            "20"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "220"
        Option          "SingleTapTimeout"      "100"
        Option          "MaxDoubleTapTime"      "180"
        Option          "LockedDrags"           "off"
        Option          "MinSpeed"              "1.10"
        Option          "MaxSpeed"              "1.30"
        Option          "AccelFactor"           "0.08"
        Option          "TapButton1"            "1"
        Option          "TapButton2"            "3"
        Option          "TapButton3"            "2"
        Option          "RTCornerButton"        "0"
        Option          "RBCornerButton"        "0"
        Option          "LTCornerButton"        "0"
        Option          "LBCornerButton"        "0"
        Option          "VertScrollDelta"       "20"
        Option          "HorizScrollDelta"      "50"
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1"
 Option          "SHMConfig"             "on"
EndSection

---

### Post by cyberdork33 on 2008-04-14
it is an option in firefox's about:config

---

### Post by ronocdh on 2008-04-15
> **cyberdork33 said:**
> it is an option in firefox's about:config
Some more information here would be awesome, as I've been having the same problem. Searching for "scroll" in the about:config doesn't yield anything that's immediately apparent to me would affect this behavior.

---

### Post by terigox on 2008-04-15
Try searching for mousewheel in your about:config as that is what firefox interprets it as.

Then find mousewheel.horizscroll.withnokey.action and change it to 0.

It's probably a similar problem listed here, except with your touch pad.

[http://ubuntuforums.org/archive/index.php/t-155511.html](http://ubuntuforums.org/archive/index.php/t-155511.html)

---

### Post by cyberdork33 on 2008-04-15
> **terigox said:**
> Try searching for mousewheel in your about:config as that is what firefox interprets it as.

Then find mousewheel.horizscroll.withnokey.action and change it to 0.

It's probably a similar problem listed here, except with your touch pad.

[http://ubuntuforums.org/archive/index.php/t-155511.html](http://ubuntuforums.org/archive/index.php/t-155511.html)I didn't know what the option would be, but that sounds like it. I always have to change the default behavior of backspace myself...

---

