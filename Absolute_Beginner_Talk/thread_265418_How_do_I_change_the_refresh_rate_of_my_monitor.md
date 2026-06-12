---
title: "How do I change the refresh rate of my monitor?"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by rrg1987 on 2006-09-25
My monitor, an old Philips 107E, is set to 1280x960 and I have an NVIDIA video card with the proprietary driver installed via Synaptic. 8)

My problem is that every time I load the resolution settings I only get 60Hz for 1280x960. :( In Windows, I have to force it to show all refresh rates so I can pick 70Hz, which works just fine. ;)

Is there a way I can force Ubuntu to up my refresh rate to 70Hz just like Windows? :confused:

Thanks! :D And sorry if this is already posted somewhere! :(

---

### Post by Mr Frosti on 2006-09-25
Turn to the documentation for your monitor and search for the vertical and horizontal sync rate. If you find the frequency ranges, add them to the "Monitor" section of the XF86Config file:

Example:
   VertRefresh 50 - 80
   HorizSync 31.0 - 100.0

From [http://www.tripos.com/index.php?family=modules,SimplePage,sybyl_stereo_on_linux&]("http://www.tripos.com/index.php?family=modules,SimplePage,sybyl_stereo_on_linux&")

If you don't know these rates, try incrementing them little by litte until you hit the refresh rate that you want.

Please note that adjusting the monitor refresh rate past the capabilities of your monitor can damage your monitor. Since it is old, it doesn't sound like too big of an issue.

---

### Post by rrg1987 on 2006-09-30
Hey, thanks! But I'm lost on how I should edit the xorg.conf file, now. :(

Mine looks like this:
```
Section "Device"
    Identifier    "NVIDIA Corporation NV20 [GeForce3]"
    Driver        "nvidia"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "PHILIPS 107E"
    Option        "DPMS"
EndSection
```Should I make it look like this:
```
Section "Device"
    Identifier    "NVIDIA Corporation NV20 [GeForce3]"
    Driver        "nvidia"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "PHILIPS 107E"
    Option        "DPMS"
    ***VertRefresh "60 - 70"***
    ***HorizSync "60 - 70***"
EndSection
```Right now, my refresh rate is 60 vertical and 60 horizontal. :(

Thanks, again! :D

---

### Post by CatKiller on 2006-09-30
That's the right place. According to [this page]("http://hoct12.stores.yahoo.net/phil107e1702.html"), the values should be >         HorizSync       30-71
        VertRefresh     50-160


---

