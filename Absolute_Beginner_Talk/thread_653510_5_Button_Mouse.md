---
title: "5 Button Mouse"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by SniperClops on 2007-12-30
Hi, I am coming from Mandriva for my desktop. How can I get all 5 buttons on my mouse to work. I am using a Microsoft Intellimouse optical. They buttons work out of the box with Mandriva but not with Ubuntu. This is the only thing keeping me from using Ubuntu.

---

### Post by SniperClops on 2007-12-30
I found [this]("http://ubuntuforums.org/showthread.php?t=93705"). So I will give that a try.

---

### Post by SniperClops on 2008-01-15
ok, here is the configuration to get the Intellimouse optical to work properly...

Section "InputDevice"
         Identifier      "Configured Mouse"
         Driver          "mouse"
         Option          "CorePointer"
         Option          "Device"        "/dev/input/mice"
         Option          "Protocol"      "ExplorerPS/2"
         Option          "ZAxisMapping"  "4 5"
         Option          "ButtonMapping" "1 2 3 6 7"
         Option          "Buttons"       "7"
EndSection

---

