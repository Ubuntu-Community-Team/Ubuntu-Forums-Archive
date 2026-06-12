---
title: "No room on my Hard Drive?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Swoop-LD on 2007-06-19
I installed Ubuntu on a separate HDD than my Windows XP system. It is 15.3 gig. Ubuntu runs well but I tried to install Google Earth and I was told that there is no room on my HDD. What the Heck?

Here is my fdisk info. What do I need to change to have access to the free space (hda1 I think)?

Thanks,

-Steve

Disk /dev/hda: 15.3 GB, 15382241280 bytes
255 heads, 63 sectors/track, 1870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1424    11438248+  83  Linux
/dev/hda2   *        1425        1847     3397747+  83  Linux
/dev/hda3            1848        1870      184747+   5  Extended
/dev/hda5            1848        1870      184716   82  Linux swap / Solaris

Disk /dev/hdb: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2490    20000893+   c  W95 FAT32 (LBA)

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9964    80035798+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS
steve@steve-desktop:~$

---

### Post by kevinlyfellow on 2007-06-19
How about you post the output of 
```
df -h
```

---

### Post by Swoop-LD on 2007-06-19
Here it is Kevinlyfellow:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             3.2G  3.0G   66M  98% /
varrun                506M   80K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  164K  9.9M   2% /proc/bus/usb
udev                   10M  164K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   17M  489M   4% /lib/modules/2.6.17-11-generic/volatile
steve@steve-desktop:~$

---

### Post by kevinlyfellow on 2007-06-20
Looks like you only partitioned off 3.2 Gigs for ubuntu.  While that is enough, it doesn't leave you much room to play around with! 

Edit: You have some options.  You can
a) Mount your /home on hda1 (giving you about 10 gigs of personal space)
b) Move your os to hda1, mount your home on hda2 (complicated) (giving you 10 gigs os space)
c) Back everything up and repartition

---

