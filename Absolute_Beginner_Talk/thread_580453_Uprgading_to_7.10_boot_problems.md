---
title: "Uprgading to 7.10 boot problems"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by spranto on 2007-10-18
Hi,

The graphical upgrade process went smoothly and everytingh went fine. When I was asked to restart, then after appearing the Ubuntu progress bar the monitor flashes a few times and it doenst't load graphically. It stops asking for login not graphically (like in the console). Can someone help please?

Thank's in advance!

---

### Post by toddward on 2007-10-19
What video card do you have?

This is an issue with the driver being incorrect for some reason.

---

### Post by spranto on 2007-10-19
It's an onboard Via one. What can i do?

---

### Post by toddward on 2007-10-19
Let's try this first, could you please give me the output of your /etc/X11/xorg.conf file?  If you really can't get it off the computer easily, the sections I'm looking for are where the video is name.  For instance, mine looks like:

```

Section "Device"
        Identifier      "nVidia Corporation NV36.1 [GeForce FX 5700 Ultra]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection
```

---

