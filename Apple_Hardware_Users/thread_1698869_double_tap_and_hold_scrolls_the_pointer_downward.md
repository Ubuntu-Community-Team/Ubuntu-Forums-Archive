---
title: "double tap and hold scrolls the pointer downward"
date: 2011-03-02
forum: Apple Hardware Users
---

### Post by miatawnt2b on 2011-03-02
Having a problem with my macbook pro.  I am using the synaptic driver in maverick with the following setup in the xorg.conf configuration.

```

    Identifier     "Mouse0"
    Driver         "synaptics"
    Option         "Protocol" "auto-dev"
    Option         "Device" "/dev/psaux"
    Option         "SendCoreEvents" "true"
    Option         "LeftEdge" "100"
    Option         "RightEdge" "1120"
    Option         "TopEdge" "50"
    Option         "BottomEdge" "310"
    Option         "FingerLow" "5"
    Option         "FingerHigh" "20"
    Option         "MaxTapTime" "100"
    Option         "MaxTapMove" "150"
    Option         "MaxDoubleTapTime" "180"
    Option         "VertScrollDelta" "20"
    Option         "HorizScrollDelta" "50"
    Option         "MinSpeed" "0.49"
    Option         "MaxSpeed" "0.78"
    Option         "AccelFactor" "0.0010"
    Option         "LockedDrags" "false"
    Option         "TapButton1" "1"
    Option         "TapButton2" "3"
    Option         "TapButton3" "2"
    Option         "VertTwoFingerScroll" "true"
    Option         "HorizTwoFingerScroll" "false"
    Option         "FastTaps" "true"
    Option         "VertEdgeScroll" "false"
    Option         "HorizEdgeScroll" "false"
    Option         "SHMConfig" "true"

EndSection
```

My problem is that when I double click and hold (as if I want to hold down the scroll arrow on a window) the actual mouse pointer will begin to scroll downward.  Any ideas on what's going on?
-J

---

