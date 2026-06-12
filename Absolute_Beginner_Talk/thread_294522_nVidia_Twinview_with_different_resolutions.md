---
title: "nVidia Twinview with different resolutions?"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by Double_Supercool on 2006-11-06
With reference to the OP in:

[http://ubuntuforums.org/showthread.php?t=73521&highlight=twinview](http://ubuntuforums.org/showthread.php?t=73521&highlight=twinview)

My understanding of Twinview is that it creates a single spanning desktop which has OpenGL capactiy.

However many of the threads I research imply that the monitor resolutions are paired (eg 1600x1200 1600x1200).

The OP in the above thread seemed to get different resolutions (by accident), however is it possible to do this 'on purpose'?

I am using a 20inch lcd widescreen (1680x1050) and a 19 inch CRT (1280x1024).

I just don't want to blow up my computer and set fire to my house . . .

---

### Post by Joe_CoT on 2006-11-06
You should be able to. I have this in my xorg.conf, in the screen section:

```
Option         "TwinView"
Option         "MetaModes" "1280x1024,1280x1024"
Option         "SecondMonitorHorizSync" "60-85"
Option         "SecondMonitorVertRefresh" "60-160"
Option         "TwinViewOrientation" "LeftOf"
```

Have you tried adding/changing your metamodes to "1680x1050,1280x1024" ?

---

### Post by Double_Supercool on 2006-11-06
Cheers mate, I will try it when I get home.

ETA.  Haven't tried the meta modes yet.  After an hour or 2 last night I actually got twinview working so that was enough for one night ;)  Now to optimize it!

---

### Post by Double_Supercool on 2006-11-07
Wahay!  Got it almost working perfectly.  I am dual spanning at the correct resolutions but all my desktop toolbars are on my right monitor, not my left.  There must be a way to define which monitor is "default" . . . 

It's a bit weird, because to get my 20 inch ws DVI viewsonic to work, I had to use a VGA adapter into the VGA out of my card, and then put a DVI adapter on my CRT and plug it into the DVI out ](*,)  Screwy monitor. 

Anyway, for those that want to know, the salient part of my xorg.conf is:


Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 68.6
    VertRefresh     43.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option         "RenderAccel"   "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "NvAGP" "1"
    Option         "TwinView"
    Option         "TwinViewOrientation" "LeftOf"
    Option         "MetaModes" "1280x1024,1680x1050"
    Option         "SecondMonitorHorizSync" "60-85"
    Option         "SecondMonitorVertRefresh" "60-160"
    Subsection "Display"
          Depth 24
    EndSubsection


I am sure this is not optimal, however it is working.  I will add/pare down as I learn more.

---

### Post by Joe_CoT on 2006-11-07
[Appendix G. Configuring TwinView](http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/README/appendix-g.html). Basically, you need to add a ConnectMonitor and Orientation line to hard code which monitor is which, so you can set the default screen. Play with it.

---

