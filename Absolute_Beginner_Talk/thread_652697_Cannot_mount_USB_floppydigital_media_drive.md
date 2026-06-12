---
title: "Cannot mount USB floppy/digital media drive"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by CT Husky on 2007-12-29
I'm a total noob, but been happily running Dapper 6.06 totally Windows-free for more than a year.  I just upgraded to 7.04.  All went well, except I can no longer use my floppy drive (Ultra 7-in1 Digital Media Drive USB 2.0 Internal Digital Media Reader).

When I put in a floppy, I hear the drive spinning and see the LED blinking, but then I get an error box with message:  "Cannot mount volume".  The details state: "you must specify the filesystem type".  Underneath is another error box, stating "Cannot mount floppy drive"

I read all the similar threads I could find before posting, but am still stumped.

The command:

```
sudo fdisk -l
```

yielded:


```
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1530    12289693+  83  Linux
/dev/sda2            9588        9964     3028252+   5  Extended
/dev/sda3            1531        9587    64717852+  83  Linux
/dev/sda5            9588        9964     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       20023   160834716   83  Linux
```

Also, BTW, the floppy worked fine in Dapper, though I never did get the other digital media readers to work.

Thanks for any help.

---

### Post by pavel989 on 2007-12-29
is this for all floppies?

---

### Post by CT Husky on 2007-12-29
Actually, no.  I had tried two disks, but after reading your response, I found a disk that I knew I had used in Dapper, and it seems to work fine.

Sorry for the bother, thanks much for the help, :oops:

---

### Post by CT Husky on 2007-12-29
Actually, I spoke too soon.  There still is something wrong, the drive is reading the contents of the first disk that is inserted after a restart, but then if I replace the first disk with a second one, it will not read any of the contents of the new disk.  

I'll fool with it a bit to see what is going on.

---

### Post by pavel989 on 2007-12-29
before removing a disk, did u first unmount or eject it on you desktop?

---

