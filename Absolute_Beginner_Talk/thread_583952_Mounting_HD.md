---
title: "Mounting HD"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by psychoflick on 2007-10-20
I have a internal HD that is not recognized by ubuntu heres what happens when I fdisk.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a0271

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c776e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24792   199141708+   5  Extended


The device I want to mount is sdb1, I'm a newbie to linux and would have thought ubuntu would have picked up my internal HD automatically. Can someone help me access it?

---

### Post by llamakc on 2007-10-20
Does

sudo mount /dev/sdb1 /mnt/

work?

---

### Post by Pumalite on 2007-10-20
Check in /media and see if sdb1 is there (disk or disk-1.etc)

---

### Post by psychoflick on 2007-10-20
mount: /dev/sdb1 already mounted or /mnt/ busy
mount: according to mtab, /dev/sdb1 is mounted on /storage

Gives that.

Checking in media there is.

cdrom  cdrom0  cdrom1  floppy  floppy0

---

### Post by psychoflick on 2007-10-20
anyone?

---

