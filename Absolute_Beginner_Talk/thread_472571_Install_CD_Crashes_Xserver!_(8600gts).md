---
title: "Install CD Crashes Xserver! (8600gts)"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by duncan_nz on 2007-06-13
My setup:

Nvidia 8600GTS 256mb
2gig ram
Athlon 64 3700 cpu


I want to install 6.10, (don't want to use 7.04 as the latest nvidia drivers will never ever install for me so I'm not bothering wasting a week on that pointless exercise again lol).

Every time I boot from the 6.10 cd, it seems to crash the x server, I tried install in safe mode and install in normal mode, but both crash it.

I think my gfx card is to new.

Anyway to get 6.10 installed? :) can I use vesa? :)

---

### Post by starcraft.man on 2007-06-13
> **duncan_nz said:**
> My setup:

Nvidia 8600GTS 256mb
2gig ram
Athlon 64 3700 cpu


I want to install 6.10, (don't want to use 7.04 as the latest nvidia drivers will never ever install for me so I'm not bothering wasting a week on that pointless exercise again lol).

Every time I boot from the 6.10 cd, it seems to crash the x server, I tried install in safe mode and install in normal mode, but both crash it.

I think my gfx card is to new.

Anyway to get 6.10 installed? :) can I use vesa? :)

Uh, yes. You can use the Vesa drivers and they should work in general. I'm not sure why 7.04 wasn't working with your drivers so I guess use whatever you think is best. Since your having trouble with the live CD I'd recommend the [alternate CD]("http://releases.ubuntu.com/6.10/ubuntu-6.10-alternate-i386.iso") from here if you continue to have trouble, it's a simple text installer always works.

---

### Post by duncan_nz on 2007-06-13
I'll try the alternative installer, hopefully the install process is the same.

I gave up on 7.04 because I want to game in linux as well as work etc, so I need the latest drivers as they perform better etc. Every time I would install them, xserver would crash. 6.10 seems better for getting the newer drivers going imo :)

---

### Post by starcraft.man on 2007-06-13
Ok well use [Envy]("http://albertomilone.com/nvidia_scripts1.html") when you get it in. It works well with most drivers. I don't really see why 7.04 should give trouble with the drivers but use what you find working.

As for the installation, alternate isn't too different. Its more hands on and allows for a lot more control of the install, I prefer it to the live install. [Here is a guide explaining it.]("http://users.bigpond.net.au/hermanzone/p14.htm")

It details how to set up a separate home partition (which I highly recommend) as well as a dual boot which you can ignore if your not doing that. It will explain each dialog if your not entirely sure what to do. It's mostly straight forward.

---

### Post by whein on 2007-06-13
I had something similar happen to me on one of my Ubuntu computers.  No matter what, I could not get 6.10 to run on the computer from either the alternate or the Live CDs.  Everything would work great up till the part where the orangish bar on the brown background appeared indicating which pieces of Gnome were starting up, and then the display would just crash.  Rows of pixels would shift randomly left or right and the system would just hang.  I wound up installing 6.06, getting the binary nvidia drivers installed, then upgrading to 6.10.  Down the road I wound up trying to put 7.04 on a different drive in the same machine and had to do similar.  That time I was able to get to a command prompt in 7.04 and manually install the nvidia drivers.  No clue what changed in the stock nvidia drivers after 6.06 but it does not play nice with my hardware.  :T
-Will
AMD Athlon 64 X2 4400+ Toledo 2.2GHz Socket 939 Processor
ABIT KN8 Ultra Socket 939 NVIDIA nForce4 Ultra ATX AMD Motherboard
EVGA 256-P2-N515-AX GeForce 7800GT 256MB GDDR3 PCI Express x16
Acer AL1917ABMD 19" 8ms DVI LCD Monitor

---

