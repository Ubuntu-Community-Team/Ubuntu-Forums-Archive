---
title: "How do I mount a USb pen Drive"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by appleimac on 2008-02-01
Hey guys can someone please help me out. I am plugging in my pen into my laptop and nothing happens.

I plug a different pen in and it works.

How do I mount the first pen that will not mount itself?


Cheers

---

### Post by NilsHG on 2008-02-01
does the stick work on other computers/ports?

---

### Post by taurus on 2008-02-01
Make sure it's plugged in, then post the outputs of these two commands from a terminal.

Applications -> Accessories -> Terminal
```
dmesg | tail
sudo fdisk -l
```

---

### Post by appleimac on 2008-02-01
```
matt@laptop:~$ dmesg | tail
[32988.992000] scsi 5:0:0:1: Direct-Access              Removable Disk   PMAP PQ: 0 ANSI: 0 CCS
[32989.220000] sd 5:0:0:0: [sdb] 4026368 512-byte hardware sectors (2062 MB)
[32989.220000] sd 5:0:0:0: [sdb] Write Protect is off
[32989.220000] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[32989.220000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[32989.224000] sd 5:0:0:0: [sdb] 4026368 512-byte hardware sectors (2062 MB)
[32989.224000] sd 5:0:0:0: [sdb] Write Protect is off
[32989.224000] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[32989.224000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[32989.224000]  sdb:


```


```
matt@laptop:~$ sudo fdisk -l
[sudo] password for matt:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa16e300e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23568   189309928+  83  Linux
/dev/sda2           23569       24321     6048472+   5  Extended
/dev/sda5           23569       24321     6048441   82  Linux swap / Solaris


```

---

### Post by appleimac on 2008-02-01
Any Ideas guys as I really want to get this working.

Many Thanks 

Matt

---

### Post by taurus on 2008-02-01
Has it worked before and do you have anything on it?

---

### Post by appleimac on 2008-02-01
The usb pen does work on my apple mac but it has never worked on my ubuntu installation.

The pen works fine in windows as well.

---

### Post by appleimac on 2008-02-01
What shoudl the pen be in /dev when it is inserted.

for example /dev/sda1


Cheers 

Matt

---

### Post by taurus on 2008-02-01
Hold it back to your windows again and see if there is a partition, /dev/sdb1, and what filesystem it is.

---

### Post by appleimac on 2008-02-01
the usb pen is FAT fielsystem.

---

### Post by reeseslover531 on 2008-02-01
it looks like from your dmesg that the drive is at sdb, so you probably can try and mount /dev/sdb1 as a fat file system.  the command would be something like mount -t vfat  /dev/sdb1  /mount/point that should work

---

### Post by appleimac on 2008-02-03
Hi there I tried what you said but I got a error.

```
matt@laptop:/mnt$ sudo mount -t vfat /dev/sdb1 /mnt/usbflash/
[sudo] password for matt:
mount: special device /dev/sdb1 does not exist
```

---

