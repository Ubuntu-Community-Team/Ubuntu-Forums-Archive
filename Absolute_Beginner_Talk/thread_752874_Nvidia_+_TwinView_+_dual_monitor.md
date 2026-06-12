---
title: "Nvidia + TwinView + dual monitor"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by csantama on 2008-04-12
I've got an nVidia graphic card and I want to set separate x screens in two monitors.
 I've tried to run nVidia settings, but there isn't the possibility of configurate two monitors. 
On the other hand, I don't know if it's better to use TwinView or Xinerama to configure x screens. When I set TwinView in xorg file both monitors work as clones with a 800x600 resolution, not as a single spanned screen.

---

### Post by .nedberg on 2008-04-12
In xorg.conf add edit your Device section to something like this (this is from my xorg.conf, your is probably a bit different, but you get the idea):

```
Section "Device"
        Identifier      "nVidia Corporation NV43 [GeForce 6600 GT]"
        Driver          "nvidia"
        Busid           "PCI:5:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "False"
        Option "Twinview" "true"
        Option "MetaModes" "1280x1024,1280x1024; 1280x1024,1024x768; 1024x768,1024x768"
        Option "SecondMonitorHorizSync" "30-65"
        Option "SecondMonitorVertRefresh" "50-75"
        Option "ConnectedMonitor" "CRT, CRT"
        Option "TwinViewOrientation" "RightOf"
EndSection
```

The MetaModes and orientation is the key to resolution and positioning

---

### Post by PinkFloyd102489 on 2008-04-12
Install nvidia-settings and run it as root. It'll do the configuring for you.

---

### Post by csantama on 2008-04-15
**None of both solutions worked**. I've still got the same problem: two monitors, one of them seems to be out of the input limit signal.
On the other hand, if I try to run *nvidia-settings* as root, I get two clone monitors at 800x600 resolution, without the possibility to change the screen resolution back to 1280x1024 and a spanned screen.

---

