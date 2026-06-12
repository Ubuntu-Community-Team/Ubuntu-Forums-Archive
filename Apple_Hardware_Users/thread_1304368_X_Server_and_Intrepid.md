---
title: "X Server and Intrepid"
date: 2009-10-29
forum: Apple Hardware Users
---

### Post by mapgie on 2009-10-29
Hey there,

I've done lots of reading around and I still can't seem to find my answer. I suspect it's probably something ridiculously easy... but my lack of any real experience doesn't allow me to know what to do.

I recently upgraded from Hardy to Intrepid on my G3 iBook (2003) (in what I thought would be an quick and easy step before upgrading to Jaunty). The installation seemed to go fine, but then I got this message:

> Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

Having said yes,

> Warning: Failsafe mode was already attempted within 30 seconds.
Warning: Falling back to gdm to report the issue.

These seem like fairly standard warnings.

> The X server is now disabled. Restard GDM when it is configured correctly.

OK, so then:

> Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) Unable to find a valid framebuffer device
(EE) Screen(s) found, but none have a usable config.

So I open a new console, sudo nano /etc/X11/xorg.conf...

> Section "Device"
Identifier "Configured Video Device"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
Modes "1024x750" "800x600" "640x480"


Any suggestions on where I can go from here?

Much thanks.

---

### Post by mapgie on 2009-10-29
Ok, so... I ended up setting up my conf so that it read: 

```
Section "Device"
       Identifier      "Configured Video Device"
       Driver          "fbdev"                 #(It was "ati" before)
       BusID           "PCI:0:16:0"
       Option          "UseFBDev"              "false"
EndSection

Section "Monitor"
       Identifier      "Configured Monitor"
       HorizSync       58-62
       VertRefresh     75-117
       Option "DPMS"
EndSection

Section "Screen"
       Identifier      "Default Screen"
       Monitor         "Configured Monitor"
       Device          "Configured Video Device"
       DefaultDepth 24
       SubSection "Display"
       Depth 24
       Modes "1024x768"
       EndSubSection
EndSection
```

(I found this at [http://ubuntuforums.org/showthread.php?t=1114297&highlight=server](http://ubuntuforums.org/showthread.php?t=1114297&highlight=server)).

I rebooted and now it opens the gdm as normal, but it won't move the mouse and it won't let me type. :(

---

