---
title: "Ubuntu Freezes"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by leetcharmer on 2007-08-11
My Feisty setup freezes randomly now and seems to boot into the terminal, and then restarts X.  I don't know why.

But, I have been hearing my hard drives make awkward starting and stopping run down sounds and my CPU Temp: 52 degrees Celsius (AMD Athlon XP 2100+).

I wanted to do a check on my hard drives, but I don't know how to use fsck properly.

I have 2 ext3 HDD's that have a / partition and swap on one, and /home on the 2nd. /dev/hda and /dev/hdb respectively.

and a FAT32 /dev/sda.

Let me know if I can give you any more information :D

---

### Post by cmnorton on 2007-08-11
If your drives are making wierd noises, that is a good place to start. Boot into level 3 (no X), and back your data up. You could always use the lUbuntu ive CD, find a USB extrnal drive, and image what's on your drives with DD or dump; or just back up data somewhere safe; get new hard-drive(s); and re-install Ubuntu.

As to running fsck, you cannot do so safely on mounted volumes. I would suggest booting your system with the Ubuntu live CD. Ensure paritions on your hard drive are not mounted (df). Run fsck on the unmounted hard-drives from an XTerm.

Strange things happen. I have had a hardware-related problem for months that continually got worse. It had to do with my Dell / Fedora 6 not wanting to boot up from power-off. To make a boring and long story short, a wireless mouse needed batteries. I felt foolish that I had suspected 1/2 a dozen other things. 

The motto of my story is certainly noting indicators as you troubleshoot, but avoiding chasing off the path each time you see a trouble indicator. You might be chasing a ghost. Perhaps you can start with checking your disks, but priority 1 for me would be getting a backup of my data.

Good Luck!

---

### Post by leetcharmer on 2007-08-11
How do I fsck my disks after booting with live CD?  Are the commands different for different filesystems?

---

### Post by cmnorton on 2007-08-12
> **leetcharmer said:**
> How do I fsck my disks after booting with live CD?  Are the commands different for different filesystems?
Sorry I did not think of this sooner:

shutdown -r -F "now"

-F will force an fsck on reboot.

<additional comments on re-editing>
I came back to edit this post, because I could not find how the Ubuntu Live Disk cached away the location my laptop's hard drive. There is a good discussion in  "Using live CD how do you mount local linux disk". I ran the Ubuntu Live Disk to try running fdsk myself. I had not previously done it. Although I could navigate to my local hard drive and the desktop navigator would go ahead and mount the volume, I needed its designator, so I could run fsck. 

If the forced fsck does not work on reboot, then I still stand by getting the data off your hard drive, using Ubuntu live disk and dd. I am an expert at neither of these, having dd'd an 80GB drive to a USB drive only once.

Good luck.

---

