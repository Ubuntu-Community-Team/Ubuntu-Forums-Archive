---
title: "Help getting External Drive Mounted"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by killaray on 2007-04-21
im on feisty fawn and have this external drive that has seized to work on any PC i have (my macbook, my xp desktop or my ubuntu desktop)

i run a dmesg and know that ubuntu is picking up the drive but it doesnt show up at all, can anyone tell me how to mount it so i could access the files?

heres the dmesg
```
[   27.092224] usb-storage: device scan complete
[   27.127516] scsi 4:0:0:0: Direct-Access     Maxtor   3200             0341 PQ: 0 ANSI: 4
[   27.128617] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[   27.129492] sdb: Write Protect is off
[   27.129495] sdb: Mode Sense: 17 00 00 00
[   27.129497] sdb: assuming drive cache: write through
[   27.130363] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[   27.131237] sdb: Write Protect is off
[   27.131239] sdb: Mode Sense: 17 00 00 00
[   27.131241] sdb: assuming drive cache: write through
[   27.131244]  sdb: sdb1
[   27.160731] sd 4:0:0:0: Attached scsi disk sdb
[   27.160770] sd 4:0:0:0: Attached scsi generic sg3 type 0

```

---

### Post by Rospo Zoppo on 2007-04-21
Please post the output of 

fdisk -l

---

### Post by killaray on 2007-04-21
here u go

```

 Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
```

---

### Post by Rospo Zoppo on 2007-04-21
I said ```
fdisk -l
``` :)

---

### Post by strandlooper on 2007-04-21
sudo fdisk -l

works for me

---

