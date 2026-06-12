---
title: "running in circles"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-11-20
I have been trying to get ubuntu (dapper) to work with a video card I just plugged in and no dice. I did apt-get install nvidia-glx and went through the process. However, when I try to reboot into x windows, it dumps me out into a shell. I have tried messing with xorg-conf but I don't know what the vertical refresh is, only the horizontal. Also, I cant get the live cd to work, I think I configured xorg.conf wrong. Does identifier have to say anything in particular or can I just call it nvidia? How do I find out my vertical refresh rate? I'm not coming up with anything on the net...

---

### Post by LLRNR on 2006-11-20
Hi I don't know how exactly to fix your problem, but here is the way you can find out a pair of ranges **monitorrange: ab-cd, ef-gh**, *ab-cd* being the HorizSync value and *ef-gh* being the VertRefresh value:

```
sudo ddcprobe | grep monitorrange
```

After installing the nVidia drivers, I called the driver listed in my xorg.conf "nvidia" instead of "nv" and then, before each login I can see the nVidia logo...

Also the LiveCD should... boot, what do you mean by "I can't get the Live CD to work" ?

---

### Post by saintj0n on 2006-11-20
When I boot the live cd, I use vesa mode, otherwise it wont even get to X windows. So, anyway, I boot it and it loads everything up and then, a wristwatch icon appears on the screen. I tried moving it around the borders and so forth but it doesn't ever actually load the gui.

sudo ddcprobe | grep monitorrange does not return anything to me but a blank line. However, ddcprobe did. 

Here's the important stuff (I think);

vbe:  Vesa 3.0 detected
oem:  NVIDIA
vendor: NVIDIA
product:   NV18 Board-p119s0nz chip rev A4
mem: 65535

timing: 640x480@60  VGA
timing: 640x480@75  Vesa
timing: 800x600@60  Vesa
timing: 1024x768@75 Vesa
ctiming: 640x480@60  
ctiming: 640x480@75  
ctiming: 800x600@85  

dtiming: 640x480@75
dtiming: 640x480@85
dtiming: 800x600@99
dtiming: 800x600@85

gamma: 1.500000

screensize: 28 21

----------------------------------------------------------
and last part of xorg.conf

section "Monitor"
      identifier   "Monitor0"
      VendorName   "Unknown"
      ModelName    "Unknown"
      Horizsync    59.0 - 61.0
      VertRefresh 50 - 150
      option        "DPMS"
EndSection

Section    "Screen"
Identifier  "NvidiaScreen"
Device      "Card0"
Monitor     "ATIMonitor"
DefaultDepth   24
SubSection    "Display"
     Depth     24
     Modes     "1024x768" "800x600" "640x480"
   EndSubSection
EndSubSection

Obviously, these aren't snapshots, but the values are the same.

---

### Post by saintj0n on 2006-11-20
Oh yeah...I almost forgot. When I switch to ctrl alt F3 and try to login, it takes my username and never asks for the password. Not sure why that's related but it obviously is.

---

