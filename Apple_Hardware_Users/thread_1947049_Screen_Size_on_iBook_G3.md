---
title: "Screen Size on iBook G3"
date: 2012-03-26
forum: Apple Hardware Users
---

### Post by ldsalomone on 2012-03-26
I recently wiped the drive on my 600mhz ibook G3 and installed ubuntu 10.04 on it. I had some troubles installing but after a few tries I got it. But after the initial boot, when gnome starts to load, the screen retreats to the upper left corner with a resolution of 800x600, leaving a wide black bar on the right and a repeat of the screen on the bottom. I have looked far and wide looking for a solution. I attempted to change my xorg.conf settings, but I cannot find it. The closest thing I have is an xorg.conf.d folder in /lib/X11/ that only contains a few unscreen related files. When I run xrandr it gives me the incorrec resolution for the screen. When I run hwinfo --monitor, I get the correct info.  I don't know much as this is my first Linux computer but I learn quick. I believe it is a hardware related problem as when I run the hardware update it says ihave no preferential hardware and gives me a list of no hardware. Any assistance is appreciated thanks.

---

### Post by ldsalomone on 2012-03-26
Also, I plan on installing a different desktop since gnome is a little heavy, possibly LXDE. But I want to solve this issue first.

---

### Post by canhoto on 2012-03-27
I have a similar problem because I can't have a 1440x900 resolution, which I should have. If I choose it (I can, using xrandr or any gui settings), I have a problem like yours, just the upper left part of the screen used and clippng part of the desktop (like if it was hiding to the outside of the screen).

I found no solution, I keep the 1280x800 resolution, which is not bad, but still...

Anyway, did you simply try to change the resolution (with xrandr changing the modes or from the screen settings?)

---

### Post by tormod on 2012-04-06
Please test on (L)Ubuntu 12.04 and file a bug report, and add a link here. I am not sure how hwinfo gets this right but the X driver could possibly find out as well then. Please attach "hwinfo --monitor" and "fbdev -i" output to the report.

EDIT: On my G4 with radeon it looks like hwinfo gets the monitor info from the PROM through /proc/device-tree. Please run "find /proc/device-tree -name EDID" and attach a copy of any resulting files.

---

