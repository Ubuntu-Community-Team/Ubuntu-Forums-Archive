---
title: "Silly mistake on installation"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by peterj on 2006-12-12
Hi, I'm a complete newbie; just re-installed but had some partition problems. I have an 80gb hard drive and I have 3 partitions, one for swap one for root, one for rest. I think I allocated them wrongly as I just ran out of diskspace.
Is there any simple way to transfer my filesystem onto the empty space? theres currently no space on the filesystem partition.
Thanks

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             2.5G  2.5G     0 100% /
varrun                220M   84K  220M   1% /var/run
varlock               220M     0  220M   0% /var/lock
procbususb             10M   96K   10M   1% /proc/bus/usb
udev                   10M   96K   10M   1% /dev
devshm                220M     0  220M   0% /dev/shm
lrm                   220M   17M  203M   8% /lib/modules/2.6.17-10-generic/volatile
/dev/hda2              61G  129M   58G   1% /media/hda1

---

### Post by bodhi.zazen on 2006-12-12
> **peterj said:**
> Hi, I'm a complete newbie; just re-installed but had some partition problems. I have an 80gb hard drive and I have 3 partitions, one for swap one for root, one for rest. I think I allocated them wrongly as I just ran out of diskspace.
Is there any simple way to transfer my filesystem onto the empty space? theres currently no space on the filesystem partition.
Thanks

GParted:
	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	
Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by patrick.dylan on 2006-12-12
Looks like the root (/) partition did nto fill the space. Since you just installed, you could reinstall and use better partition sizes this time.

---

