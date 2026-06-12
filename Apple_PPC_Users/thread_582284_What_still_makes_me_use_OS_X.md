---
title: "What still makes me use OS X"
date: 2007-10-19
forum: Apple PPC Users
---

### Post by bodobuntu on 2007-10-19
Hi folks :)

Great, I installed Gutsy Gibbon without a single problem from an alternative CD, 
on my ibook G4 1.42Ghz, 14" 512MB RAM

It made my font rendering better than what it was on Feisty.
Also I can select WPA from network manager.

BUT I have two problems that keep me on os x :(

1) Trackpad: I can't whatever I set in xorg.conf use it as I use it in os x, it doesn't follow my fingers really... sometimes it's slow some other times it's fast.
Some times it clicks when i didn't wanted to tap on the trackpad. As if it was "too" sensitive.

2) Wifi: I got wifi working with my appleairport2 firmware that i retrieved from my OSX install, BUT it works only for a little distance (about two meters if not less)

Did you please managed to fix these problems? can I see your xorg.config and how you had your touchpad obey to your finger tips?
Any clue for my wifi problems please?

Thank you :)

P.S. Here's a part of my xorg.conf about the touchpad:
Section "InputDevice"
    Identifier    "SynapticsTouchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/input/mice"
    Option        "Device"        "/dev/input/appletouch"
    Option        "Protocol"        "auto-dev"
    Option        "LeftEdge"        "50"
    Option        "RightEdge"        "900"           #max 950
    Option        "TopEdge"        "30"
    Option        "BottomEdge"        "304"           #max 334
    Option        "FingerLow"        "55"#15
    Option        "FingerHigh"        "60"#20
    Option        "MaxTapTime"        "200"#180
    Option        "MaxTapMove"        "200"
    Option        "MaxDoubleTapTime"    "180"
    Option        "ClickTime"        "300"
    Option        "FastTaps"        "0"
    Option        "VertScrollDelta"    "30"
    Option        "HorizScrollDelta"    "30"
    Option        "EdgeMotionMinZ"    "30"
    Option        "EdgeMotionMaxZ"    "160"
    Option        "EdgeMotionMinSpeed"    "1"
    Option        "EdgeMotionMaxSpeed"    "400"
    Option        "EdgeMotionUseAlways"    "false"
    Option        "MinSpeed"        "0.2" #0.2
    Option        "MaxSpeed"        "2.0" #2.0
    Option        "AccelFactor"        "0.12"#0.12
    Option        "LockedDrags"        "false"
    Option        "RTCornerButton"    "0"
    Option        "RBCornerButton"    "0"
    Option        "LTCornerButton"    "0"
    Option        "LBCornerButton"    "0"
    Option        "TapButton1"        "1"
    Option        "TapButton2"        "2"
    Option        "TapButton3"        "3"
    Option        "CircularScrolling"    "1"
    Option        "CircScrollDelta"    "0.1"
    Option        "CircScrollTrigger"    "1"
    Option        "PalmDetect"        "true"    # not supported
    Option        "CoastingSpeed"        "1"
    Option        "SHMConfig"        "on"
    Option	      "VertTwoFingerScroll" 	"1"
    Option	      "HorizTwoFingerScroll" 	"1"
EndSection

---

### Post by SycloneMedia on 2007-10-20
You might be having problems with your trackpad because you have waaaay too many options set,  especially if you don't know what they do.

For example:

If you don't want the tap clicking, you have

Option "TapButton1" "1"
Option "TapButton2" "2"
Option "TapButton3" "3"

but you should set all three of those to "0". Then, it won't tap anymore. ;)

Did you back up your old xorg file ? You really should get rid of all the extra options you set, and start with just the tap buttons to "0" and also why are there "#" symbols next to your speed settings?

Start from there (scratch) and only add options that you learn about first, not just everything someone else might have shown you from their xorg file. That's a recipe for problems.

Hope that helps a little...

---

