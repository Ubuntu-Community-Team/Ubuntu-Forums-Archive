---
title: "Partitioning a hardware raid on HPT RR2220"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Droidling on 2008-01-05
I believe I have finally got my Highpoint Rocketraid 2220 installed. I have 2 x 400GiB drives configured as a JOB array that GParted is currently partitioning. The main array is 6 x 750GiB drives in a RAID 5 configuration.  I set both of these up using the RAID  BIOS  utility. When I select this array (sda) in GParted it displays a negative size (-647672517632.00B) that has no relation to the 3750GiB that I was expecting.  It looks likes it might let me create a partition but says the new max size is -617667MiB. This looks a little like the result of a numeric overflow. I wasn't brave enough to try it.  I tried dmsg and fdisk -l to get a little more info.  Most of this looks normal to me. Fdisk lists sda with 0 cylinders, with the comment "You must set cylinders."  I understand fdisk can set this, but what do I set it to?

terry@terry-desktop:~$ dmesg | grep 'sda:'
[17179589.324000] SCSI device sda: 7324958720 512-byte hdwr sectors (3750379 MB)
[17179589.324000] sda: Write Protect is off
[17179589.324000] sda: Mode Sense: 2f 00 00 00
[17179589.324000] SCSI device sda: drive cache: write back
[17179589.324000] SCSI device sda: 7324958720 512-byte hdwr sectors (3750379 MB)
[17179589.324000] sda: Write Protect is off
[17179589.324000] sda: Mode Sense: 2f 00 00 00
[17179589.324000] SCSI device sda: drive cache: write back
[17179589.324000]  sda:<6>NET: Registered protocol family 17
.
.
.
terry@terry-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       19080   153260068+  83  Linux
/dev/hdc2           19081       19457     3028252+   5  Extended
/dev/hdc5           19081       19457     3028221   82  Linux swap / Solaris
You must set cylinders.
You can do this from the extra functions menu.

Disk /dev/sda: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 799.9 GB, 799937658880 bytes
255 heads, 63 sectors/track, 97253 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       97253   781184691   83  Linux

It is possible I still don't have the drivers properly installed. I can post the terminal output from building and installing the drivers if someone thinks that is the issue.

Sorry for the long read

Terry

---

