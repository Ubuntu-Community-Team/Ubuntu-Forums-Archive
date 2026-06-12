---
title: "How to make your own Bootable Linux CD (with your own apps) on 1CD?"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-02-17
Hi,

I would like to make my own CD with some few apps like K3B and some apps I am using. 
I am installing Ubuntu as server, that 's the first step.
  Then install  the fluxbox +xorg and so on. Ok
   Install K3B . OK
   
  
So, now, how to make it available as a Knoppix for instance on one CD ?
  
Thank you very much, 

Greetings

Patrick

---

### Post by souteneur3190 on 2006-02-17
yah, i always wondered this, any ideas?

---

### Post by Qrk on 2006-02-18
SLAX or PCLinuxOS (I think) both let you do this fairly easily. SLAX has modules you can use, whereas PCLinuxOS lets you boot into it, then save the changes.

SLAX has great documentation, too.

---

### Post by cotcot on 2006-02-18
SLAX did not work with me. I added some apps as modules and made a new iso but after burning this iso to a CD (with K3B burn image) it does not boot.

---

### Post by patrick295767 on 2006-02-18
If found more info.... 
from houseofmore
 
>  Default  Re: can I remaster the K(ubuntu) live cd?
check out bootcd in the repo. haven't used it myself, but sounds up that way.

"bootcd - run your system from cd without need for disks
Build an image of your running Debian System with the command bootcdwrite.
You can also build a bootcd ISO image via NFS on a remote System.
When you run your system from CD you do not need any disks. All
changes will be done in ram. To reuse this changes at next boot time
you can save them on FLOPPY with the command bootcdflopcp. If booting
from your CD-drive is not supported, booting from FLOPPY is possible.
It is possible to install a new system from the running CD with the
command bootcd2disk. Bootcd2disk can also find a target disk, format
it and make it bootable automatically. Bootcd also supports lilo,
grub, initrd root fs, devfs, transparent-compression ISO 9660 fs and
syslinux/isolinux."  
   
And this too:
[http://www.ubuntuforums.org/showthread.php?t=19428&highlight=bootcd](http://www.ubuntuforums.org/showthread.php?t=19428&highlight=bootcd)
   
Progressing a bit...

---

