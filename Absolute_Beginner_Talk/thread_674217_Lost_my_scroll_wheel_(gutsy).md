---
title: "Lost my scroll wheel (gutsy)"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by bucketoftruth on 2008-01-21
Suddenly my scroll wheel doesn't work any more.  It's a basic MS Wheelmouse.

Relevant section of xorg.conf
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

What can I do to get my scroll wheel back?

---

### Post by JeremyStein on 2008-01-21
What has changed?  Does it work under windows?

---

### Post by bucketoftruth on 2008-01-21
I haven't changed anything.  It still works when I boot to windows and on other machines.

---

### Post by bucketoftruth on 2008-01-22
I have no idea what happened, but I booted up when I returned home this evening and it works again.  I hate mysteries.

---

