---
title: "how do i get a 2nd internal HDD to work"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by catroaring on 2008-03-02
i have a 2nd internal HHD which does not show up in computer.  also an external HDD that does not as well.  I think i should take baby steps and work on the internal drive first i guess.

this is my output from fdisk -l


   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19222   154400683+  83  Linux
/dev/hda2           19223       19457     1887637+   5  Extended
/dev/hda5           19223       19457     1887606   82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14945   120045681    7  HPFS/NTFS

Disk /dev/sda: 20.0 GB, 20000267776 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131    0  Empty
/dev/sda2               6        2431    19486845    b  W95 FAT32


the first device is my system install HDD , works fine
the second is the internal that doesn't show up
the third is my ipod, shows up fine

tx for any help

---

### Post by punx45 on 2008-03-02
the fact that it is in the list is a good sign, the system can see the disk.   If you have added it after inital install it probably has no mounting instructions in /etc/fstab, so the disk is not mounted.   it also appears to be NTFS which may be a problem (im not too up to date with the newer versions is additional software still required for NTFS?)

type mount to see a list of partitions that are currently mounted.
check out the man page for mount to find out how to mount the drive, then if you are successful, you can add the drive to /etc/fstab and the drive will mount when the computer is booted.

---

