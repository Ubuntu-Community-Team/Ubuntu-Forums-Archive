---
title: "[SOLVED] Dual disk - but can't see one of them"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by g7kse on 2007-12-07
This sounds like a trivial thing but I'm bright enough to sort it out...

I've installed gutsy on one drive 9primary one) and have XP on a secondary one. Everything boots nicely through GRUB...but

How do I see the windows drive through the Ubuntu file manager? 

Is it something to do with mounting the other drive. they're both identical SATA if that make a difference

---

### Post by shadow-of-sin on 2007-12-07
See here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by g7kse on 2007-12-07
when I did the fisk-l I got this:


Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc68581cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24416   196121488+  83  Linux
/dev/sda2           24417       24792     3020220    5  Extended
/dev/sda5           24417       24792     3020188+  82  Linux swap / Solaris
~$

No mention of the other disk as NTFS any suggestions?

---

### Post by Duck2006 on 2007-12-07
If you boot from the live CD and do

sudo fdisk -l

and see if you can see the other drive.

---

### Post by Niniel on 2007-12-07
2 identical disks sounds like a RAID setup... maybe you need a driver?

---

### Post by shadow-of-sin on 2007-12-07
> when I did the fisk-l I got this:


Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc68581cf

Device Boot Start End Blocks Id System
/dev/sda1 * 1 24416 196121488+ 83 Linux
/dev/sda2 24417 24792 3020220 5 Extended
/dev/sda5 24417 24792 3020188+ 82 Linux swap / Solaris
Did you type:
```
sudo fdisk -l
```
?

When I omit the "sudo" on my computer the command shows no output...

---

### Post by g7kse on 2007-12-07
Ok so using live disk now

This time I get 

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc68581cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24416   196121488+  83  Linux
/dev/sda2           24417       24792     3020220    5  Extended
/dev/sda5           24417       24792     3020188+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00042d84

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24791   199133676    7  HPFS/NTFS

Oh and yes I did sudo fdisk-l the first time, sorry

---

### Post by Duck2006 on 2007-12-07
When you went though the steps from

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Did you use (hdx,y) or (sdx,y)?

---

### Post by g7kse on 2007-12-07
> **Duck2006 said:**
> When you went though the steps from

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Did you use (hdx,y) or (sdx,y)?

I used sdx,y because I thought that was right

---

### Post by g7kse on 2007-12-07
Since going back to the installed version and doing those commands again Duck 2006, The drive hasn't exactly reappeared but I can access it through the file manager

and the sudo fdisk -l output is

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24416   196121488+  83  Linux
/dev/sda2           24417       24792     3020220    5  Extended
/dev/sda5           24417       24792     3020188+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00042d84

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24791   199133676    7  HPFS/NTFS


so i think I have inadvertently solved it. Thanks very much for your help

Alex

---

### Post by Duck2006 on 2007-12-07
Any more questions just ask. Good to see you can see then.

---

### Post by nikoPSK on 2007-12-07
Please mark this thread as SOLVED

---

