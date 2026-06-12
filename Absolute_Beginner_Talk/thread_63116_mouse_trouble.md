---
title: "mouse trouble"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by NaOH on 2005-09-07
So I setup linux with my microsoft, corded, intellimouse.  Recently I've come across a logitech v500 wireless mouse, but i can not get ubuntu to recognize this device, what shall i do?  thanks

---

### Post by jshein on 2005-09-27
I am running breezy on an Acer TravelMate 4400. The V500 was detected automatically.

here is the relevant area from xorg.conf

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

---

### Post by N6546R on 2005-09-29
A data point, running Hoary on an IBM T42 Thinkpad. Just picked up a V500 and was impressed and pleased that all I had to do was put a battery in it an plug it in. Everything just worked.

Perry

---

### Post by SilentCacophony on 2005-09-29
Or you could try to reconfigure X:

[B]sudo dpkg-reconfigure xserver-xorg
[/B]
and answer the questions carefully.

---

