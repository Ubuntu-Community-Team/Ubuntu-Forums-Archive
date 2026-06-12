---
title: "Dual Montiors"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by goTUX! on 2006-10-10
Hello

Introducing myself as a new member to UBUNTU forums, just decided to install Ubuntu and I love it! I think I'm going to be using it a lot compared to windows, however a couple of things im finding hard...

I would like to use Dual Monitors, but i am aware this is complicated to do in Ubuntu (well for me anyway :D). I have read a few threads somewhere about this issue which require editing the xorg.conf file.

If someone could tell me step by step how to do this in laymans terms it would be greatly appreciated, because i dont understand most of the jargon in the guides ive read so far.

I have a nVIDIA FX5200 graphics card which has a VGA and a DVI output on the back and 2 monitors
- Do I need to find out which PCI BUS it is connected to? If so how?
- How do I find out the name of my Monitor or doesnt it matter what i call it?
- What sections do i need to change in xorg.conf to get it to see the other monitor?

Thanks in advance for your help

---

### Post by bodhi.zazen on 2006-10-10
> **goTUX! said:**
> Hello

Introducing myself as a new member to UBUNTU forums, just decided to install Ubuntu and I love it! I think I'm going to be using it a lot compared to windows, however a couple of things im finding hard...

I would like to use Dual Monitors, but i am aware this is complicated to do in Ubuntu (well for me anyway :D). I have read a few threads somewhere about this issue which require editing the xorg.conf file.

If someone could tell me step by step how to do this in laymans terms it would be greatly appreciated, because i dont understand most of the jargon in the guides ive read so far.

I have a nVIDIA FX5200 graphics card which has a VGA and a DVI output on the back and 2 monitors
- Do I need to find out which PCI BUS it is connected to? If so how?
- How do I find out the name of my Monitor or doesnt it matter what i call it?
- What sections do i need to change in xorg.conf to get it to see the other monitor?

Thanks in advance for your help

This is my best effort:

[How to Dual Monitor](http://ubuntuforums.org/showthread.php?t=240150)

If I can be of assistance, PM or ask in this thread.

---

### Post by goTUX! on 2006-10-10
Thanks for the reply, but i still dont understand everything in that guide...i have tried it already with no luck.
How do i find out the Bus ID and the horizontal and vertical refresh rates of my monitors?

Sorry if im sounding thick, i just dont understand :(

---

### Post by bodhi.zazen on 2006-10-10
First the monitor: Google search or post you monitor.

Second: Have you installed the nvidia drivers?

Third: You will need an adapter for your DVI output.

Try this:```
lspci -X | grep VGA
```

Hold while I find a thread .....

This thread may help:

[Previous thread](http://ubuntuforums.org/showthread.php?t=257317&highlight=monitors)

---

### Post by goTUX! on 2006-10-10
Thanks bodhi.zazen

i got it to work, its backwards coz it thinks my monitors are the other way round but i know how to do it now :)

---

### Post by bodhi.zazen on 2006-10-10
> **goTUX! said:**
> Thanks bodhi.zazen

i got it to work, its backwards coz it thinks my monitors are the other way round but i know how to do it now :)

Do you know how to fix that?

Change```
# ************************************************** ********************
# Server section
# ************************************************** ********************

# ************************************************** ********************
# Graphics device section
# ************************************************** ********************

#
################################################## ############################################
#
# T W I N V I E W - S E T U P (NVIDIA)
#
# Monitor1 and Monitor2 are both connected to the same (nvidia) videocard
# activates the nvidia-twinview-mode
#
# advantage: opengl on both windows
# disadvantage: cant get 1600x1200 on each monitor, it seems that both
# screen must have same refreshrates
# no xv for mplayer

Section "Device"
Identifier "twinview"
VideoRam 256000
VendorName "nVidia Corporation"
BoardName "Video device"
Driver "nvidia"
BusID "PCI:1:0:0"
Screen 0
Option "TwinView"
Option "MetaModes" "1600x1200,1600x1200"
**Option "TwinViewOrientation" "LeftOf"**
Option "SecondMonitorHorizSync""UseEdidFreqs"
Option "SecondMonitorVertRefresh" "UseEdidFreqs"
Option "HWCursor" "On"
Option "UseEdidFreqs" "true"
Option "NvAGP" "1"
# Option "NoLogo" "true"
# Option "RenderAccel" "true"
# Option "CursorShadow" "true"
# Option "XvmcUsesTextures" "true"
EndSection
```

To:```
# ************************************************** ********************
# Server section
# ************************************************** ********************

# ************************************************** ********************
# Graphics device section
# ************************************************** ********************

#
################################################## ############################################
#
# T W I N V I E W - S E T U P (NVIDIA)
#
# Monitor1 and Monitor2 are both connected to the same (nvidia) videocard
# activates the nvidia-twinview-mode
#
# advantage: opengl on both windows
# disadvantage: cant get 1600x1200 on each monitor, it seems that both
# screen must have same refreshrates
# no xv for mplayer

Section "Device"
Identifier "twinview"
VideoRam 256000
VendorName "nVidia Corporation"
BoardName "Video device"
Driver "nvidia"
BusID "PCI:1:0:0"
Screen 0
Option "TwinView"
Option "MetaModes" "1600x1200,1600x1200"
[size=2]**Option "TwinViewOrientation" "RightOf"[/size]**
Option "SecondMonitorHorizSync""UseEdidFreqs"
Option "SecondMonitorVertRefresh" "UseEdidFreqs"
Option "HWCursor" "On"
Option "UseEdidFreqs" "true"
Option "NvAGP" "1"
# Option "NoLogo" "true"
# Option "RenderAccel" "true"
# Option "CursorShadow" "true"
# Option "XvmcUsesTextures" "true"
EndSection
```

---

### Post by goTUX! on 2006-10-10
Thanks! :mrgreen:

---

