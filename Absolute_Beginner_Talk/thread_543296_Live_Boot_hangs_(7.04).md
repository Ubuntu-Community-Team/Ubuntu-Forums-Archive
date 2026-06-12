---
title: "Live Boot hangs (7.04)"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by boxmonkey on 2007-09-04
Hello,

I'm pretty new to Linux in general, I have used Ubuntu on a few occasions before but my experience is extremely limited, especially when it comes to installing.

I am ultimately trying to install Ubuntu but I can't even get the live CD part to boot on my machine. The progress bar goes back and forth for a while then the CD spins down, and then sometimes it just hangs doing nothing (I've given it over 20 minutes just to be sure) and other times the display corrupts.

I suspect I need to include some special drivers on another CD, using the driver CD option in the boot menu, but I don't know how to begin doing that.

If it helps at all, here is my system:
Asus P5B-E
SATA drives
SATA DVD burner
GeForce 7600 GS

I have tried booting with the SATA drives in IDE mode, it did not make a difference at all. I suspect it's the video card, but I tried forcing it to run the install at the lowest resolution VGA mode but that didn't work either... Any ideas?

---

### Post by ConradPafford on 2007-09-05
Recommended RAM minimum of 256 MB for standard install but alternative cd is available - not sure where but there is one I heard - Sorry I have no more information for you.
Might consider CDROM or RAM problem - Please enter all specs as it makes it easier for the experienced ones to solve.

Good day,

Conrad

---

### Post by boxmonkey on 2007-09-05
Hi,

It looks like it was a memory issue, of sorts! I had memory remapping turned on in the BIOS. As soon as I turned that off I was able to get in to Ubuntu.

I have 3GB of ram and my MB allocates a whole gig to PCI.

---

### Post by ConradPafford on 2007-09-06
SWEET - glad you are into the world of freedom and out of the world of control!
As far as the memory allocation goes -- you should be able to modify that in the bios (assuming that it is allocated for video ram)
I dream of having an external card for all my ubuntu machines .... just too dang broke!

---

