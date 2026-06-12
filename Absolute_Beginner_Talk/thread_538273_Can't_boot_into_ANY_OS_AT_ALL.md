---
title: "Can't boot into ANY OS AT ALL"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by mikecomua on 2007-08-29
Hello, I have a 120gb Seagate external drive, which I decided to install Ubuntu on (for no reason). So one day I have decided to boot into Ubuntu and it said something about my hard drive being mounted 35 times and it had to check it. SO then it gave me an error message and said I couldn't boot. After that I booted into XP and tried to make my Csaid partition smaller, using Norton Partition Magic, but it gave me an error message, so I couldn't do that either, Now I can't boot into Xp AND Ubuntu. Now I booted into Ubuntu Live CD and tried to partition my external drive to backup my data, but it said
Quote:
GParted 0.2.5

Resize /dev/sdb1 from 108.92 GiB to 18.29 GiB ( ERROR )

check filesystem on /dev/sdb1 for errors and (if possible) fix them ( ERROR )

e2fsck -f -y -v /dev/sdb1

/dev/sdb1 is mounted.
e2fsck 1.40-WIP (14-Nov-2006)
e2fsck: Cannot continue, aborting.



========================================

Create Primary Partition #1 (ext3, 90.63 GiB) on /dev/sdb

========================================
How should I
a) bring back my Windows drive to life
b) bring my UBuntu to live
Thx a lot

---

### Post by chuckyp on 2007-08-30
To bring the windows drive to life boot to the windows cd.  Select recovery mode and 
```

fixmbr c:

```

That way you atleast have something working.  More info is needed though as far as fixing ubuntu.  Were you using grub?  if so you could try reinstalling it via live cd.  Mount the drive and chroot to it etc...

---

