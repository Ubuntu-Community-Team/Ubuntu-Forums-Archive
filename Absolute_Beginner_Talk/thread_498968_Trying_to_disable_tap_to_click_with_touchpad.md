---
title: "Trying to disable tap to click with touchpad"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by climbjm on 2007-07-12
I installed "Synaptics TouchPad driver for XOrg/XFree86" and was reading on their website, [http://web.telia.com/~u89404340/touchpad/index.html](http://web.telia.com/~u89404340/touchpad/index.html).

[FONT="Lucida Console"][INDENT]How can I configure tap-to-click behavior?

   1. If you set MaxTapTime=0 in the X config file then the touchpad will not use tapping at all, i.e. touching/tapping will not be taken as a mouse click.
   2. If, instead, you set MaxTapMove=0 in the X config file, then the touchpad will not use tapping for a single finger tap (left mouse button click) but will for the two and three finger tap (middle and right button click).[/INDENT][/FONT]

Does anyone know what this X config file they are talking about is?

---

### Post by AJB2K3 on 2007-07-12
etc/x11/xorg.conf
use
> sudo gedit /etc/X11/xorg.conf
mine does not have that setting so i would assume you need to add
> Option		"MaxTapMove"	"0"
for that to work.
Can anyone conform be for i add it?

---

### Post by climbjm on 2007-07-12
I figured it out.

They were talking about /etc/X11/xorg.conf

Also, once i restarted Ubuntu, it worked!

---

### Post by climbjm on 2007-07-12
Also, it did disable my double tap.

It drove me nuts because I use the mouse a ton (I grew up on windows, yeah yeah I know, I am trying my hardest to switch) and I type a lot, and when I typed, I kept double tapping on accident and it would mess up everything.

---

### Post by jordanmthomas on 2007-07-12
I know you got what you wanted, but if you're interested in more options, here's my xorg.conf with all the options:
```
Section "InputDevice"
    Identifier          "Mouse3"
    Driver              "synaptics"

        Option      "Device"                "/dev/psaux"
    Option      "Protocol"              "auto-dev"
    Option      "LeftEdge"              "120"
    Option      "RightEdge"             "830"
    Option      "TopEdge"               "120"
    Option      "BottomEdge"            "560"  # comment out this entire line to disable horizontal scroll/click ability
    Option      "FingerLow"             "14"
    Option      "FingerHigh"            "15"
    Option      "EmulateMidButtonTime"  "70"
    Option      "VertScrollDelta"       "20"
    Option      "HorizScrollDelta"      "0"
    Option      "MaxTapTime"            "0"    # 0 disables tap-to-click, set it to 100 to re-enable
    Option      "MinSpeed"              "0.3"
    Option      "MaxSpeed"              "0.75"
    Option      "AccelFactor"           "0.015"
    Option      "EdgeMotionMinSpeed"    "200"
    Option      "EdgeMotionMaxSpeed"    "200"
    Option      "UpDownScrolling"       "1"
    Option      "LeftRightScrolling"    "0"
    Option      "CircularScrolling"     "0"

#Option         "SendCoreEvents"        "true"
#    Option             "Device"                "/dev/psaux"
#    Option             "Protocol"              "auto-dev"
#    Option             "HorizScrollDelta"      "0"
    Option              "SHMConfig"             "on"
    # For ALPS TouchPads
#    Option             "MaxSpeed"              "0.7"
#    Option             "MinSpeed"              "0.18"
#    Option             "AccelFactor"           "0.08"
#    Option             "TopEdge"               "120"
#    Option             "LeftEdge"              "120"
#    Option             "BottomEdge"            "830"
#    Option             "RightEdge"             "650"
#   Option              "FingerLow"             "25"
#    Option             "FingerHigh"            "30"
    # Do you keep moving the mouse while typing? Try this trick.
    #synclient TouchpadOff=1 disable your synaptics touchpad
    #synclient TouchpadOff=0 enable your synaptics touchpad
EndSection
```

have fun.

---

### Post by tcoffeep on 2007-07-12
I prefer to d/l gsynaptics

> sudo apt-get gsynaptics

then all you do is add :

> SHMConifg = "true"

to your touchpad entry in xorg.conf

---

