---
title: "Annoying Feisty problems"
date: 2007-04-24
forum: Apple Intel Users
---

### Post by Shen on 2007-04-24
I dist-upgraded to Feisty on my MacBook last weekend. It's not bad, lots of stuff works that didn't work before, but perhaps they did a bit too much!

First of all, I can't get gsynaptics to work:

```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
```

yet my xorg.conf has both the lines:

```
        Option          "SHMConfig"     "true"
        Option          "SHMConfig"     "on"
```

I'd like to change a few things, as I keep clicking accidentally touching the touchpad.

Secondly, the internal accelerometer appears to be registered as a joystick. Which is good. But whenever I use mplayer, it reads the joystick and the movie jumps around all over the place. Is there a way to stop mplayer from doing that, or turn the accelerometer off?

Thanks

---

### Post by rhebert on 2007-04-24
"Option" "SHMConfig" "true" looks good.  I don't know about the "on" line, you might want to remove it.  What does the rest of that section look like?

---

### Post by Shen on 2007-04-24
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"

        Option          "LeftEdge"      "100"
        Option          "RightEdge"     "1120"
        Option          "TopEdge"       "50"
        Option          "BottomEdge"    "310"

        Option          "FingerLow"     "25"
        Option          "FingerHigh"    "30"

        Option          "MaxTapMove"    "220"

        Option          "TapButton1"    "1"
        Option          "TapButton2"    "3"
        Option          "TapButton3"    "2"

        Option          "MinSpeed"      "0.79"
        Option          "MaxSpeed"      "0.88"
        Option          "AccelFactor"   "0.0015"

        Option          "SHMConfig"     "true"
        Option          "SHMConfig"     "on"
EndSection
```

I got the "on" bit from a thread on these forums. It doesn't work with any combination of the two, though.

---

