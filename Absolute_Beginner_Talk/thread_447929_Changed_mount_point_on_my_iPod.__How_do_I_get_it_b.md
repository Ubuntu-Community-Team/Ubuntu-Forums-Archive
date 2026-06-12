---
title: "Changed mount point on my iPod.  How do I get it back?"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Captain Slack on 2007-05-18
Last night, I was trying to get my iPod set up with gtkpod.  It automounted to a different directory than gtkpod wanted to use, so I went into the properties of the device and found a place where I could set the mount point.  I set this to /media/iPod and saved my change.  When I did, the iPod icon disappeared from the desktop.  I pulled my sync cable, plugged it back in, and got the an error message saying I'd put an invalid character in the mount point.  No problem to fix normally, but it didn't give me the icon back, so I can't fix it!! 

Where do I go to correct or delete my change so I can get my iPod to be seen by Ubuntu (7.04) again?

---

### Post by Najand on 2007-05-18
Make a /media/iPod folder:
```

sudo mkdir /media/iPod

```

---

### Post by Captain Slack on 2007-05-18
I had that already.

---

### Post by Najand on 2007-05-18
Copy/paste your /etc/fstab here.

---

### Post by Captain Slack on 2007-05-18
Here ya go:

>  /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=41e00265-9e98-4bda-88cb-db207af3f10f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=F280DF0980DED369 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=F4A5-4335  /storage1       vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=F062-1F5C  /storage2       vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=e2be8e25-7424-4243-b7dd-a926c33e3342 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/floppy0  auto    rw,user,noauto  0       0


---

### Post by Najand on 2007-05-19
What is the output of:
```

sudo fdisk -l

```
when you have plugged it to your computer?

---

### Post by medicineman24 on 2007-05-21
I have the exact same problem:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=065f610e-b5ed-43f6-ae7b-091efe7290f9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=cd4b2be2-89b1-45bf-8dd5-3029634fa8e6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Please help. Thanks in advance.

---

### Post by medicineman24 on 2007-05-21
This is my fdisk:
> sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14405   115708131   83  Linux
/dev/sda2           14406       14593     1510110    5  Extended
/dev/sda5           14406       14593     1510078+  82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 1015 MB, 1015021568 bytes
32 heads, 61 sectors/track, 253 cylinders
Units = cylinders of 1952 * 2048 = 3997696 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      398636      983425  2283019262   72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(398635, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(983424, 30, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       86419     1078237  3872056480   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(86418, 26, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1078236, 17, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      957932     1949749  3872056384   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(957931, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1949748, 25, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?     1478321     1478349      110998    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(1478320, 8, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1478348, 22, 13)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


---

### Post by medicineman24 on 2007-05-21
Solved it.  I plugged in iPod, restarted machine, changed mount point to just IPOD and did the same in gtkpod.  I don't know why it worked but i think capitalizations may have been the prob. mabe "/i" is some newline character that i wouldn't know about.

---

