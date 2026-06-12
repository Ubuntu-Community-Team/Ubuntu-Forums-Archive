---
title: "iMac Screen alignment in 7.10"
date: 2007-12-07
forum: Apple PPC Users
---

### Post by linuxun on 2007-12-07
I have an iMac 20", non-intel, pre-isight.

I installed 6.10 and updated to 7.04.  Everything worked great.
I upgraded (gksudo "update-manager -c") to 7.10 and now have a screen alignment issue.

Basically the desktop is shifted to the right about a quarter inch and that quarter inch wraps around to the left side of my screen.  To get the cursor to that area, I have to push the cursor off the right edge of the screen.

Other than this, the upgrade is working perfectly.  The iMac has a nvidia 5200 card and is running in 1680x1050.  Here is that section of the xorg.conf.

Any ideas on how to get the screen to align?  -Thanks

```
Section "Device"
    Identifier    "nvidia 5200"
    Driver        "nv"
    BusID        "PCI:240:16:0"
EndSection

Section "Monitor"
    Identifier    "Apple 20 inch"
    Option        "DPMS"
    HorizSync    28-84
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nvidia 5200"
    Monitor        "Apple 20 inch"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by stream303 on 2008-01-21
I have this same issue on mine with 7.10, however I'm starting to think it is not ubuntu specific, nor ppc specific after seeing some of the same reports with stand-alone monitors.  Could be an X11 issue, but I'm not sure.

I have tried XVIDTUNE to tweak modelines, but the screen just stays rock solid with a very slight right-hand shift.

I'm living with it for now by just using a solid color background, and making sure that I don't maximize apps, and just stretch them myself.  I don't like it, but it isn't a showstopper, especially when it doesn't seem like it is just a matter of editing xorg.conf.  I think there is a deeper problem...

---

