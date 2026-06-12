---
title: "screen resolution (nvidia onboard)"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by randomjohn on 2007-08-26
I'm running Feisty on an old Gateway machine. 

Hardware info reports the chip is NV15BR [GeForce2 Ultra, Bladerunner]

I log in via SSH and UltraVNC.  When I try to change the resolution, it only allows me 800x600 and 640x480.  Any suggestions, please?  I just want 1024x768

---

### Post by randomjohn on 2007-08-26
and for what it's worth, 1024 x 768 is the first resolution that shows up in the "Screen" section of xorg.conf for all of the various depths.

Can I delete the monitor information, since the monitor that was there when I installed feisty is no longer there?

---

### Post by wallyhall on 2007-08-30
Some (hopefully) helpful links:

[https://help.ubuntu.com/community/FixVideoResolutionHowto#head-c7979448ab81077f16349d3ca4be7aa5a5a52de2]("https://help.ubuntu.com/community/FixVideoResolutionHowto#head-c7979448ab81077f16349d3ca4be7aa5a5a52de2") -- describes how to use debconf (Debian's package configuration program, used also in Ubuntu), that should get you back to an xorg.conf like what Ubuntu ships with.

[http://ubuntuforums.org/showthread.php?p=1773584](http://ubuntuforums.org/showthread.php?p=1773584) - describes an easy way of running the nvidia-setings program, a superb tool that comes with the more recent propriety nvidia drivers, lets you setup your graphics card easier than if it were on Windows (without touching a single configuration file b hand!)

Hope it helps.

---

### Post by steve.horsley on 2007-08-30
It may be just playing safe because it can't read the monitor itself to find the supported scan frequencies. I have in the past found that entering the horizontal and vertical scan rates for the non-existent monitor (we use a KVM switch) into the xorg.conf file allow X to use a more sensible resolution.

Add HorizSync and VertRefresh to your monitor section similar to below. Remember that plugging a real monitor in if the frequencies are wrong could damage a CRT monitor.

```
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        HorizSync    30-107
        VertRefresh  48-120
EndSection
```

---

