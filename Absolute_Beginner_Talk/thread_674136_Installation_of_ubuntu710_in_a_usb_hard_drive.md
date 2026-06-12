---
title: "Installation of ubuntu710 in a usb hard drive"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by lkoyk on 2008-01-21
I have installed Ubuntu 7.10 in my external usb disk (320Gb) and  I want to repartition the disk where linux is installed (ext2 partition) in order to take advantage of the unused disk space for back ups and other storage reasons. Is it possible to do it now or I should have done it at first? What I can do now?

---

### Post by duruttye on 2008-01-21
In order to repartition a disk, you must first unmount it.
In your case you can manage it by loading a live cd, there you can start the disk partitioner called gparted and partition the disk again.

I'm no expert here and I don't know if you will have to mess around with fstab.
Maybe someone more skillful can help you with that.


Good luck!

---

### Post by logos34 on 2008-01-21
You say 'unused disk space'...if you mean empty space INSIDE the root partition, then you'll need to use gparted from the live cd (ubuntu or Gparted), as duruttye said, to shrink it--root can't be mounted.  If, on the other hand it is literally unsused/unallocated/unpartitioned, then you can simply fire up Gparted:

gksudo gparted

Afterwards [create a mount point and add it to fstab]("http://www.psychocats.net/ubuntu/mountlinux").

---

### Post by lkoyk on 2008-01-21
When I say unused space, I mean empty space! I have allready an installation of Ubuntu in my external drive and I have the Gparted program, but I don't know how to use it in order to redistribute the empty space and create a new partition let's say a fat32 to be seen from windows.

---

### Post by duruttye on 2008-01-21
Again: when you want to partition something, it has to be unmounted.
If you only have an ubuntu installation on your external usb drive then you have to use the LiveCd.

After boot start Gparted.
Then right click on  the partition that you want to shrink. Unmount it, if it is mounted, then resize/move, then move the slidebar where you want it to be. Remember, the ubuntu needs at least 4Gb space.
After you're done, apply the changes.
And somewhere along you will be able to select the file system type you want.

It make take a long time, too.

Good luck!

---

### Post by duruttye on 2008-01-21
Oh, I forgot, that after the resizing, there will be an unused space among the partitions, there you should select something like make new partition.

---

### Post by lkoyk on 2008-01-22
Ok I'll try it Thanks for your help! I hadn't understood that I should use the live cd again!

---

