---
title: "Why does Ubuntu hate iBook/Powerbook trackpads?"
date: 2006-07-24
forum: Apple PPC Users
---

### Post by zachws on 2006-07-24
This problem has been going on for the longest, through a lot of kernel updates and Ubuntu updates. Why does the mouse go so slow on many Mac laptops (i.e. the trackpad)?

At present the best fix is the following (added to xorg.conf):
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "LeftEdge"              "120"
        Option          "RightEdge"             "830"
        Option          "TopEdge"               "120"
        Option          "BottomEdge"            "650"
        Option          "FingerLow"             "14"
        Option          "FingerHigh"            "15"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "110"
        Option          "EmulateMidButtonTime"  "75"
        Option          "VertScrollDelta"       "20"
        Option          "HorizScrollDelta"      "20"
        Option          "MinSpeed"              "0.3"
        Option          "MaxSpeed"              "0.75"
        Option          "AccelFactor"           "0.015"
        Option          "EdgeMotionMinSpeed"    "200"
        Option          "EdgeMotionMaxSpeed"    "200"
        Option          "UpDownScrolling"       "1"
        Option          "CircularScrolling"     "1"
        Option          "CircScrollDelta"       "0.1"
        Option          "CircScrollTrigger"     "2"
EndSection
```

Any ideas? It really affects the usability of Ubuntu for many PPC users. Wouldn't this be an easy fix?

Thanks.

Idea :-k :
Would the latest release of Xorg fix this? (As this is xorg.conf)
Can we expect a fix?

---

