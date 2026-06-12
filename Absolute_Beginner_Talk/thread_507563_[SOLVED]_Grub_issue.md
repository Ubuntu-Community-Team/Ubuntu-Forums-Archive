---
title: "[SOLVED] Grub issue"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Lord Grover on 2007-07-23
*First post; please be gentle.*

Ubuntu's installed and working fine :)

However, when I try to start Windoze I get:
```
Error 12: Invalid device requested.
Press any key to continue.
```

I'm guessing there's something wrong here:
```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        8857    71087625    f  W95 Ext'd (LBA)
/dev/sda3           13985       19452    43921408    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4            8858       13984    41182627+  83  Linux
/dev/sda5   *           8        8632    69280281    7  HPFS/NTFS
/dev/sda6            8633        8857     1807281   82  Linux swap / Solaris
```
or here:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Windows XP Media Center Edition
root            (hd0,4)
savedefault
makeactive
chainloader     +1
```

I've already fiddled with it, as you may be able to tell; originally the boot device was set to /dev/sda3, which is the old D: drive in windows, the C: (root) drive is /dev/sda5. Similarly, I've amended menu.lst to ,4 from ,2

Any ideas gratefully received.

---

### Post by spydon on 2007-07-23
Shouldn't it be a 5 where the 4 is?

```

root            (hd0,5)

```

---

### Post by Lord Grover on 2007-07-23
> **spydon said:**
> Shouldn't it be a 5 where the 4 is?

```

root            (hd0,5)

```

Don't think so, assuming starting at zero is correct.

---

### Post by spydon on 2007-07-23
Isn't C: on:
```
/dev/sda5   *           8        8632    69280281    7  HPFS/NTFS
```?

If I remember right the second number is the partition and the first number is the device...

---

### Post by Lord Grover on 2007-07-23
> **spydon said:**
> Isn't C: on:
```
/dev/sda5   *           8        8632    69280281    7  HPFS/NTFS
```?

If I remember right the second number is the partition and the first number is the device...
Yep. That's what I think. Doesn't work though. :(

I think I'll zap the disk and reinstall windoze & ubuntu from scratch unless anyone has any bright ideas ...

---

### Post by spydon on 2007-07-23
```
root            (hd0,5)
```
Should it maybe be sd instead of hd then?

---

### Post by logos34 on 2007-07-23
Here's a detailed explanation of your problem:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#12_](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#12_)

EDIT: (hd0,4) is correct-->sda5.  It's the fact that the your boot windows MCE is on a logical partition that's the issue.

---

### Post by Lord Grover on 2007-07-23
Coolio. At least I have an answer, thanks logos34. 
It's a new installation so nothing much to lose with a repartition and re-install.

Cheers,

---

