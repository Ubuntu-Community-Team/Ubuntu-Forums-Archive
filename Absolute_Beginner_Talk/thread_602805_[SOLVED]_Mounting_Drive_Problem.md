---
title: "[SOLVED] Mounting Drive Problem"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by mdpalow on 2007-11-04
Hi  all,

To the point.

I have an extra drive that was 90gigs and formatted to ext3 and worked fine in Ubuntu 7.10 until a short while ago.

I decided I wanted to try something out, so I reduced the 90gig partition (using gparted) to 80gigs and then created a new partition that was 10 gigs and used fat32 file type.

Now, I can see the 10gig partition in Nautilus, but the 80gig partition is missing. It's not showing up in /media although the 10gig is...

I tried to update fstab with the drive, but that doesn't work. 

In terminal, trying to mount using 'mount /dev/sdb1' gives me an error telling me the mount point is missing. The new 10gig partition has a mount point '/media/disk' and the 80gig is missing mount point when I look at it in gparted.

So, bottom line is 80 gig is no where to be found. I know it's there. Reducing its size and adding a fat32 partition to the end shouldn't do this; should it?

Thanks in advance to anyone who want to chime in...


fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008e04f

Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        2440    19599268+  83  Linux
/dev/sda2            2441       14598    97659135   83  Linux
/dev/sda3           38549       38913     2931862+  82  Linux swap / Solaris
/dev/sda4           14599       38548   192378375   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a6765f5

Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1       10913    87658641   83  Linux
/dev/sdb2           10914       12188    10241437+   b  W95 FAT32

---

### Post by Pumalite on 2007-11-04
Use Gparted Live CD and take another look.

---

### Post by sisco311 on 2007-11-04
to mount manually your partition:
```
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
```to automount the partition on boot you must edit your /etc/fstab file

---

### Post by mdpalow on 2007-11-04
Thank you sisco311.

That did the trick.

I undid the partition I made hoping it would put it back. When I booted up again it still didn't show. I then saw your posting and was able to get it to work. I'm gonna partition that little bit again and see if I can use your tip to finally get it to work.

Thanks again for your timely reply, you're the man. 

Funny signature btw... lol

---

### Post by sisco311 on 2007-11-04
you're welcome. 
here are some links about fstab:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

