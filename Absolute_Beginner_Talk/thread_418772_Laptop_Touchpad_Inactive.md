---
title: "Laptop Touchpad Inactive"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by jpoRS on 2007-04-22
Hey,

I have a HP Pavilion running Feisty.  Everything is working great (for once) EXCEPT for the touch pad mouse.  It stopped working a day or two after I updated to Feisty, so I don't THINK that is it, but who knows.  I am currently using a USB mouse, and that works fine, but I need the touch pad back for when I take my laptop to class.

Any ideas?

jim

---

### Post by annda on 2007-04-22
does the touchpad work if you reboot your computer without the usb mouse attached?

if so, please post your /etc/X11/xorg.conf file.

---

### Post by jpoRS on 2007-04-22
No, rebooting without the USB doesn't make a difference.  Here is xorg.conf anyway though.

The first part shows up with or without the USB hooked up.

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection


jim

---

### Post by Bachstelze on 2007-04-22
When you're asked to paste a file, it's the **whole** file !

---

### Post by jpoRS on 2007-04-22
A thousand pardons Hymn, I just posted the part I thought was relevant because the whole file is quite large.  If you have anything you would like to see specifically, I would be  glad to provide that.

---

