---
title: "Cannot change monitor resolution after installing ATI driver"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by tarek on 2007-06-23
Hi,

I installed ATI driver + beryl and everything works but the max resolution I can get is 1024x768. I added 1152x867 but it doesn't show up in Gnome menu -> .. -> Screen Resolution.

This is the monitor and screen sections of the xorg.conf file:

```
Section "Monitor"
  Identifier  "KM-718"
  Option    "DPMS"
EndSection

Section "Screen"
  Identifier  "Default Screen"
  Device    "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
  Monitor   "KM-718"
  DefaultDepth  24
  SubSection "Display"
    Depth   24
    Modes   "1152x867" "1024x768" "800x600" "640x480"
  EndSubSection
EndSection

```

Before install the ATI driver I was able to use higher resolution

Anybody has any idea why?

Thanks
tk

---

### Post by BobCFC on 2007-06-24
Well you want **1152x864** not 1152x867

I had lots of trouble with gnome resolution but fortunately nvidia drivers come with a great nvidia-settings program that fixed it for me.  Is there anything similar with ati?  Try typing ati at the terminal then pressing tab a few times to look for ati commands.

Also the refresh rates might by causing problems.

---

### Post by tarek on 2007-06-24
damn typo... thanks, it works now but the refresh rate is only 60, it should be 75. Any idea how to change that?

Thanks again,
TK

---

### Post by BobCFC on 2007-06-24
You can specify ranges for the refresh rate in the monitor section above DPMS... but it is VERY IMPORTANT that you do not put wrong values because of possible **damage** to monitor.  

You will have to seach for the frequencies of **your model** exactly but you would add them similar to below.

```

Section "Monitor"
    ...
    HorizSync    31.0 - 80.0
    VertRefresh  58.0 - 75.0
    Option       "DPMS"
EndSection
```

---

### Post by tarek on 2007-06-24
Sweet ... I checked the manufacturer website and got the right rates, it works now.

Thanks a lot!
TK

---

