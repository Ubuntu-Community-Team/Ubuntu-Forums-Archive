---
title: "g4 powerbook trackpad"
date: 2006-07-10
forum: Apple PPC Users
---

### Post by Digitallysick on 2006-07-10
Ok everyone, what is the best G4 Powerbook Trackpad setup for xorg.conf

this is what i have now, and the tap click is annoying, and the pad doesnt track well, any advice?

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

---

