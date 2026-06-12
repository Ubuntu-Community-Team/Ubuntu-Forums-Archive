---
title: "Viewing Hard Drive Partitions"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by bigdawg72987 on 2007-03-24
I recently repartitioned my hard drive for a dual boot with ubuntu and winXP.  I have a 60Gb HDD and gave 20 to XP and the rest for ubuntu.  When installing ubuntu I let it create the partitions itself.  I know the XP partition is 20Gb but when I am using nautilus it only tells me I have ~30Gb free space.  There is 10Gb somewhere I don't know.  What commands can I use to see where that partition is and what it is being used for?

---

### Post by taurus on 2007-03-24
Post the output of this command from a terminal here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by bigdawg72987 on 2007-03-25
sudo fdisk -l
Password:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        7099    36539842+  83  Linux
/dev/sda3            7100        7296     1582402+   5  Extended
/dev/sda5            7100        7296     1582371   82  Linux swap / Solaris

How does this breakdown into sizes?

---

### Post by taurus on 2007-03-25
What about 

```
df -h
```

---

### Post by bigdawg72987 on 2007-03-25
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              35G  6.8G   26G  21% /
varrun                506M   88K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  140K  9.9M   2% /proc/bus/usb
udev                   10M  140K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-11-generic/volatile
/dev/sda1              20G   14G  6.0G  70% /mnt/win

---

### Post by taurus on 2007-03-25
Well, your /dev/sda2 is about 35GB and it's about 26GB free.  It means that Ubuntu takes up about 10GB of space.  And don't forget, swap partition takes up some space too.

```
free
```

---

### Post by bigdawg72987 on 2007-03-25
free
             total       used       free     shared    buffers     cached
Mem:       1035552    1021100      14452          0      44480     673340
-/+ buffers/cache:     303280     732272
Swap:      1582360      17548    1564812


on a side note....how do I make the code in the pretty box?

---

### Post by taurus on 2007-03-25
> **bigdawg72987 said:**
> free
             total       used       free     shared    buffers     cached
Mem:       1035552    1021100      14452          0      44480     673340
-/+ buffers/cache:     303280     732272
Swap:      1582360      17548    1564812


Looks like you have 1.5GB of swap. 

> on a side note....how do I make the code in the pretty box?

You would start with a square bracket, [, then include the word code and then close it with another bracket, ].  When you are done typing in whatever you want to type in there, do the same except this time, put the / in front of the word code.

---

