---
title: "A new trackpad challenge!"
date: 2007-06-25
forum: Apple Intel Users
---

### Post by gamblorius on 2007-06-25
Hi all,

I recently installed Feisty on my 17inch R1 MBP. A lot of stuff works great out of the box, however I am having difficulty getting the trackpad to behave the way I want. In Mac OS X, there is a trackpad configuration option that reads "Place two fingers on trackpad and click button for secondary click." Basically, one places two fingers on the trackpad, throwing a "switch" that causes any clicks of the physical trackpad button to register as right rather than left clicks.

 I have successfully gotten my trackpad to perform right clicks via two-finger taping under Ubuntu, but I used to use the OS X two finger "switching" option a lot, and I would love to get it working under Linux. I have scoured the synaptics driver info to no avail--it seems like this should be possible as the driver _can_ register when two fingers are on the trackpad. Anyway, any help on this is welcome. My xorg synaptics section is below if it helps. Thanks!

```

Section "InputDevice"
       Identifier   "Synaptics Touchpad"
       Driver   "synaptics"
       Option  "SendCoreEvents"        "true"
       Option  "Device"        "/dev/psaux"
       Option  "Protocol"      "auto-dev"
       Option  "LeftEdge"      "150"
       Option  "RightEdge"     "1070"
       Option  "TopEdge"       "100"
       Option  "BottomEdge"    "310"
       Option  "FingerLow"     "25"
       Option  "FingerHigh"    "30"
       Option  "MaxTapTime"    "180"
       Option  "MaxTapMove"    "220"
       Option  "MaxDoubleTapTime"      "180"
       Option  "HorizEdgeScroll" "0"
       Option  "VertEdgeScroll" "0"
       Option  "TapButton1"            "0"
       Option  "TapButton2"            "0"
       Option  "TapButton3"            "0"
       Option  "LockedDrags"           "off"
       Option  "VertScrollDelta"       "20"
       Option  "HorizScrollDelta"      "50"
       Option  "VertTwoFingerScroll"  "1"
       Option  "HorizTwoFingerScroll" "1"
       Option  "MinSpeed"      "1.10"
       Option  "MaxSpeed"      "1.30"
       Option  "AccelFactor"   "0.08"
       Option  "Emulate3Buttons"       "true"
       Option  "SHMConfig"     "on"
# corner buttons
        Option "RTCornerButton" "0"
        Option "RBCornerButton" "2"
        Option "LTCornerButton" "0"
        Option "LBCornerButton" "3"
EndSection

```

---

### Post by ivesjd on 2007-06-25
I use this alot in OS X as well. And would love to know if anyone has gotten working.

---

### Post by ubu4ever on 2007-06-25
I have been looking all over the web for the exact same thing for the past hours ...
I have a macbook and would be glad to have this behavior working under ubuntu.

---

### Post by ronocdh on 2007-06-25
Hm, I much prefer the ctrl+click or the hold-click methods. I also cannot stand tapping, and install G/QSynaptics just to disable it!

---

### Post by ivesjd on 2007-06-26
What I meant was two fingers on the touchpad and then click the mouse button. I love that in OS X. I hate tapping as well.

---

### Post by gamblorius on 2007-06-26
Glad to know there are others like me! I felt like I was crazy for not liking to tap. I hope that someone knows how  to make it work.

---

### Post by ivesjd on 2007-07-01
Maybe no one knows of a way to do this.

---

### Post by K3ITHK on 2007-07-02
Not really sure if this will help. I still have not been able to get Ubuntu installed due to a serious lack of time. Hope to do it soon.

Anyway
[http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Touchpad](http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Touchpad)

---

### Post by dragonwings on 2007-07-02
on my macbook i do a (three finger ) tap on the pad for a right click

---

### Post by russo.mic on 2007-07-02
I would also like to chime in that I would LOVE to get 2 finger + click function in Ubuntu.
I hate tapping.

Anybody have any ideas, as I've tried about every configuration of xorg.conf to get this to work!

Russo

---

### Post by ubu4ever on 2007-07-06
From the synaptics driver main developer.:


No, the driver can't do that.

Unfortunately I don't have much free time to work on the driver these days.

-- 
Peter Osterlund

I guess we are on our own for this one ...

---

