---
title: "Lenovo R61i mouse scroll"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by alphabyte on 2008-04-16
I have a brand new Lenovo R61i and I wanted to know how to set up the red track point (ibm red mouse thingy) so that the middle button will scroll. Also, is it possible to set up a scroll feature on the mouse pad itself? 
Thanks,
~Alphabyte

---

### Post by spiderbatdad on 2008-04-16
The edge of the touchpad should scroll.
The system may not be detecting your hardware properly. Read through dmesg ( run in the terminal.) You may need an additional boot parameter to get the trackpoint/touchpad working correctly. There have also been updates to the drivers, available from sourceforge...dmesg will provide a link near the end of the output.

Near the top of the output, look for a message that might say, "apic disabled by system bios." And further down...try adding 'lapic.'

---

### Post by kaptengu on 2008-04-16
In /etc/X11/xorg.conf in the mouse section, add:
```
        Option          "EmulateWheel"          "true"
        Option          "EmulateWheelButton"    "2" 

```
Restart gnome (ctrl-alt-backspace), and middle button scrolling should work.
Works on my X41.

---

### Post by alphabyte on 2008-04-16
Well that worked GREAT for the keyboad red mouse thingy. Now if only i can figure out the scroll situation on the actual mouse pad. Thank you!
-Alphabyte

---

### Post by kaptengu on 2008-04-16
I think you can find the answer here:
[http://www.thinkwiki.org/wiki/Category:R61](http://www.thinkwiki.org/wiki/Category:R61)
I don't have the UltraNav thing, so this is the best I can do.
Good luck.

---

### Post by GeneralCody on 2008-05-08
> **alphabyte said:**
> Well that worked GREAT for the keyboad red mouse thingy. Now if only i can figure out the scroll situation on the actual mouse pad. Thank you!
-Alphabyte

Personnaly, I only use the Trackpoint, but if you enable both in the BIOS, you could just add some lines to xorg.conf...

Here's my version of the section:

The reason for all the stuff for the Trackpoint is that I can now use the middle mousebutton to scroll, plus use it as a third mouse button to paste from clipboard etc.
It also works dandy when connecting an ordinary usb wheelmouse...

```

# This is for the Trackpoint ( red thingie )
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "Emulate3Buttons"       "on"
        Option          "Emulate3TimeOut"     "50"
        Option          "EmulateWheel"  "on"
        Option          "EmulateWheelTimeOut" "200"
        Option          "EmulateWheelbutton"    "2"
        Option          "YAxisMapping" "4 5"
        Option          "XAxisMapping" "6 7"
        Option          "ZAxisMapping" "4 5"
EndSection

# This is for the Trackpad ( the thing you bump into while lying on the couch )
Section "InputDevice"
Option "XAxisMapping" "6 7"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

```To get the vertical scrolling, just enable it in the mouse prefs in Ubuntu...

---

