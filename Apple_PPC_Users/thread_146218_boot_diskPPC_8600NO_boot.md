---
title: "boot disk:PPC 8600:NO boot"
date: 2006-03-17
forum: Apple PPC Users
---

### Post by qwarrior on 2006-03-17
Thanks in advance for this,

I have an "Vintage ;-)" PPC 8600/300 A/V.  It is a true OLD world Mac.  I've had YDL 2.0 on it before and went thru the process of creating an "old world boot disk", meaning I couldn't use YDL's yaboot facility.

I have the Ubuntu Macintosh install CD that was given to me by an office mate, but it will not boot.

Any ideas as how to proceed?

I have a commercial cd of Mac OS 8.5 and the 8600 has now problem with booting with it. 

So, I figure it has something to do with the way Macintosh reads in cd devices during boot.

Thanks again.

qwarrior

---

### Post by ristosu on 2006-04-02
One way would be to use BootX. First you have to install Mac OS 8.5 in a small partition (a few hundred MB will be consumed for this), and leave the rest unallocated (to be used for Ubuntu).

Then boot into Mac OS, install BootX from [http://penguinppc.org/bootloaders/bootx/](http://penguinppc.org/bootloaders/bootx/), copy kernel and initrd images from Ubuntu CD into /System Folder/Linux Kernels, run BootX, and choose Linux.

Later, when successfully installed, you could try to install quik, to avoid booting via Mac OS.

---

