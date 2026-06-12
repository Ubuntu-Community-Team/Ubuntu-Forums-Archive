---
title: "Dual Boot Problem"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by ghicking on 2007-05-01
Hi all

I'm dual-booting on twin sata drives.  Following the loss of the XP mbr, I could not boot into linux (Ubuntu) or XP.  I reinstalled Ubuntu Edgy from the Live CD, but it could not see the other drive with XP so didn.t write it into the GRUB.  I upgraded to Feisty to see if that would trigger something, but no dice. I then discovered that the SATA cable plugs were cracked.  A new pair of cables sorted out that problem, but I still couldn't boot into XP.  I then came across Super Grub Disk, downloaded the ISO and wrote it to a floppy.  When I reboot to the floppy I get 'GRUB'  (Not 'GRUB >') and the computer hangs.  Has anyone found a similar problem and also a solution.

Graham

---

### Post by confused57 on 2007-05-01
> **ghicking said:**
> Hi all

I'm dual-booting on twin sata drives.  Following the loss of the XP mbr, I could not boot into linux (Ubuntu) or XP.  I reinstalled Ubuntu Edgy from the Live CD, but it could not see the other drive with XP so didn.t write it into the GRUB.  I upgraded to Feisty to see if that would trigger something, but no dice. I then discovered that the SATA cable plugs were cracked.  A new pair of cables sorted out that problem, but I still couldn't boot into XP.  I then came across Super Grub Disk, downloaded the ISO and wrote it to a floppy.  When I reboot to the floppy I get 'GRUB'  (Not 'GRUB >') and the computer hangs.  Has anyone found a similar problem and also a solution.

Graham

Boot into Ubuntu and post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Does the drive with XP boot, if you boot to it first?

---

### Post by Doug11 on 2007-05-01
You may find this post useful

[http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot)

---

### Post by ghicking on 2007-05-02
Thanks confused57

No, I can't boot XP at all

Here is the fdisk output

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sdb4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Thanks!
Graham

---

