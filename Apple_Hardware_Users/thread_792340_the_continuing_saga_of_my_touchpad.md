---
title: "the continuing saga of my touchpad"
date: 2008-05-12
forum: Apple Hardware Users
---

### Post by eschmidt90 on 2008-05-12
Okay, not so long ago I posted an issue with my unfortunate lack of a right click.  Well, it occured to me that an upgrade from 7.10 to 8.04 might do the trick, and now I've gone from functional but inconveniant to inconveniant and unfunctional.

Here's how it went down:

I installed (succesfully) 8.04.  I rebooted.  I logged in and tapped two fingers on my touchpad and low and behold, it right-clicked.  I was amazed!  Well, I got some work done and had to leave the room, so I shut the lid on my laptop.  I opened it back up, and I tried to right click to find that this no longer functioned.  I was back to how it was in 7.10.  I decided to try to fix this by re-booting.  after all, in 7.10 closing the lid caused all sorts back-light issues, so maybe the mouse could be fixed by re-booting as well.

Ubuntu started back up.  I logged in and now my touchpad will not go where I want it.  It will move in teh right direction, but if my finger comes off the pad and then touches it again, the mouse will jump to the opposite side of teh screen.  I have a wide screen, so I do need to lift my finger on occasion to navigate.

HEre's where it gets weird.  BEfore I log in, teh mouse has no problems whatsoever.

Any ideas?

-------------------------EDIT----------------------------

I am using an intel macbook.

---

### Post by mcoyle on 2008-05-13
Try this. Trackpad settings are stored in the /etc/X11/xorg.conf file. Find the "Snyaptics Touchpad" section, comment it out, and replace it with the code below.

It removes one finger tap, but keeps two finger tap and two finger scroll.

Hope it works for ya.

Michael


```


Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "SHMConfig"     "on"
        Option          "LeftEdge"      "10"
        Option          "RightEdge"     "1200"
        Option          "TopEdge"       "10"
        Option          "BottomEdge"    "370"
        Option          "FingerLow"     "10"
        Option          "FingerHigh"    "15"
        Option          "MaxTapTime"    "180"
        Option          "MaxTapMove"    "220"
        Option          "SingleTapTimeout"      "100"
        Option          "MaxDoubleTapTime"      "180"
        Option          "LockedDrags"   "off"
        Option          "MinSpeed"      "1.10"
        Option          "MaxSpeed"      "1.30"
        Option          "AccelFactor"   "0.08"
        Option          "TapButton1"    "0"
        Option          "TapButton2"    "3"
        Option          "TapButton3"    "2"
        Option          "RTCornerButton"        "0"
        Option          "RBCornerButton"        "0"
        Option          "LTCornerButton"        "0"
        Option          "LBCornerButton"        "0"
        Option          "VertScrollDelta"       "20"
        Option          "HorizScrollDelta"      "50"
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "0"
EndSection




```

---

### Post by eschmidt90 on 2008-05-13
Ready for the stunning result?

This did not function.  Two fingered right clicks still fail to work.  Here's the kicker, one fingered taps still move the cursor to the place on teh screen corresponding to the place on the touchpad I tap.

I'm fairly computer savy, even with low level, and this is really starting to fustrate me.  It worked when I first installed, and promptly stopped.

I don't understand why this is happening.

---

### Post by cyberdork33 on 2008-05-13
First, you should not really just copy and paste the entire config from the how to, rather you should selectively pick and choose the options that you want (and the ones that work) adjusting them for your preferences.


Are you on a Macbook or Macbook Pro? The Macbook Pros now have the mutitouch pads and they do not work with synaptic.

---

### Post by eschmidt90 on 2008-05-13
I am on just a macbook

I understand about copying what I want.  But here's teh deal - changing xorg.conf doesn't seem to have any effect on what my computer does.  Its not an issue of getting it to do what I want, its an issue of getting it to change its behavior at all!

I change xorg.conf to reflect suggestions, and I reboot (an easy way to restart X11) and no change occurs.

FRUSTURATING!

---

### Post by cyberdork33 on 2008-05-13
You might have a look at this bug report. There are a lot of things to try. Basically, some of the other tools that update the xorg.conf can break the touchpad, so you have to make sure certain things are still there.

[https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/173411](https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/173411)

---

