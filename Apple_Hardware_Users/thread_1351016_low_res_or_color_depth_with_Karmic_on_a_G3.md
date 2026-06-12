---
title: "low res or color depth with Karmic on a G3"
date: 2009-12-09
forum: Apple Hardware Users
---

### Post by grundygreen on 2009-12-09
Went looking fo xorg.conf but it nowhere to found.
Read somewhere Karmic handles things differently.
Any ideas?
BTW seems to loading down the system. I'm betting once video is fixed it will be a little peppier.:confused:

---

### Post by linuxopjemac on 2009-12-10
which model ? Please be more precise.

---

### Post by ajgreeny on 2009-12-10
If you make an /etc/X11/xorg.conf file, it will be loaded at boot time, but as you say there isn't one by default.  I had to do that for karmic, with my ati 9200SE card which will not run smoothly or with compiz, unless I use 16 bit colour, or a lower resolution than the monitor's native 1280x1024.

Here's my xorg.conf for karmic, which works well, though I am still not very happy with karmic's graphics, and run jaunty as my main system.

> Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

I hope this helps sort out your problem.

---

### Post by grundygreen on 2009-12-10
I believe it is a bondi blue. ATI video

---

### Post by grundygreen on 2009-12-10
> **ajgreeny said:**
> If you make an /etc/X11/xorg.conf file, it will be loaded at boot time, but as you say there isn't one by default.  I had to do that for karmic, with my ati 9200SE card which will not run smoothly or with compiz, unless I use 16 bit colour, or a lower resolution than the monitor's native 1280x1024.

Here's my xorg.conf for karmic, which works well, though I am still not very happy with karmic's graphics, and run jaunty as my main system.



I hope this helps sort out your problem.

Jaunty just powers down on bootup.
At lest the g3 is usable with karmic.

---

### Post by linuxopjemac on 2009-12-11
```
Section "InputDevice" 
Identifier "Generic Keyboard" 
Driver "kbd" 
Option "XkbRules" "xorg" 
Option "XkbModel" "pc105" 
# European keyboard is "pc 105" if you have an imac keyboard " and @ are reversed
# Option "XkbModel" "pc104" 
# USA keyboard is "pc 104" 
Option "XkbLayout" "gb" 
# Great Briton keyboard is "gb" 
Option "XkbLayout" "us" 
# USA keyboard is "us" 
Option "XkbOptions" "lv3:lwin_switch" 
EndSection

Section "InputDevice" 
Identifier "Configured Mouse" 
Driver "mouse" 
EndSection

Section "Device" 
Identifier "Configured Video Device" 
BusID "PCI:0:18:0" 
Option "UseFBDev" "true" 
EndSection

Section "Monitor" 
Identifier "Configured Monitor" 
HorizSync 58-62
VertRefresh 75-117
EndSection

Section "Screen" 
Identifier "Default Screen" 
Monitor "Configured Monitor" 
EndSection

Section "Module" 
Disable "glx" 
Disable "dri" 
EndSection


```

---

### Post by grundygreen on 2009-12-11
Will try that.
Ajgreeny's xorg.conf helped but wasn't perfect.
It is definatly a xorg.conf issue.
May have to do some tweaking.

I wish we knew more about the the new x scheme in karmic.

---

