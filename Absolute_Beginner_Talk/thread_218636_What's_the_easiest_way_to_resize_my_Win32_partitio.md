---
title: "What's the easiest way to resize my Win32 partition?"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-07-18
QTParted isn't doing the trick.  I am running from the root terminal (doesn't work when run normally).  When I open it, there is an error message displayed to the effect of "Cannot unmount parittion device please do so by hand first to commit changes!"  I click "OK" anyway and go into the GUI.  The "resize" buttons are shaded out on my main Linux ext3 partition and on my Windows XP NTFS partition.  Why is this?

---

### Post by benuski on 2006-07-18
NTFS is pretty much impossible to resize right now.  There are some experimental and beta drivers out there that are getting better and better, but nothing included in Ubuntu yet.  And I may be wrong, but I don't think ext3 supports resizing after it has been set.  And even if it does, you can only grow and shrink at the end of the partition, not at the beginning, because all the important stuff that runs your partition, like the boot record, sit at the very beginning of the partition.  Thats why people who dual boot, like me, cannot resize their partitions after they're first set, cause the windows partition is first in line, then the linux one.

I hope that made some sense

---

### Post by aysiu on 2006-07-18
I've had no problems resizing NTFS partitions.

Resizing isn't experimental, nor is reading.

The only things experimental right now is writing to NTFS.

QTParted is a piece of crap and frequently grays out options that should not be grayed out. I would suggest using DiskDrake, which is available on [the PCLinuxOS live CD.](http://ftp.belnet.be/linux/pclinuxos/live-cd/english/preview/)

Read more [here](http://www.ubuntuforums.org/showthread.php?p=637340).

---

### Post by fatsheep on 2006-07-18
Thanks for the link I will check it out. :)

---

### Post by mrvw0169 on 2006-07-19
Or you can always use gParted [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) which for me is the best tool for all file systems (and seems actually to be "actively" improved)... It really is superior to QTParted and looks better...

I'm guessing you're using Kubuntu but even when I'm stuck with only the Kubuntu LiveCD (my Ubuntu one is dead) the first thing I need to do is sudo aptitude install gparted =P since QTParted grays out resize most of the time...

---

