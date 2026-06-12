---
title: "Synaptic Touchpad Config"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by jordan43022 on 2007-04-06
Ok, so I'm trying to get my highly annoying touch pad (synaptic) to simply turn off!

I've done some looking around and they all the walkthroughs I can find say to go to xorg.conf and find this area:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection

The only problem is that my file has:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CoprePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"      "4 5"
        Option          "Emulate3Buttons"             "true"
EndSection

I'm sure I have the synaptic drivers installed and that I am, in fact, using a synaptic mouse.  This is the only "mouse" field I have.... Lil' help?  I'm using 6.10

---

### Post by xopher on 2007-04-06
This might be helpful: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

