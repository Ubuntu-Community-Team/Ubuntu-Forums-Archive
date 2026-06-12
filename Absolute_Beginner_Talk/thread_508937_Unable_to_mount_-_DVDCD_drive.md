---
title: "Unable to mount - DVD/CD drive"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by DarkMana on 2007-07-24
When I attempt to navigate to my DVD/CD drive in File Browser (listed as "CD-ROM 1"), I get the following error:

> Unable to mount the selected volume.
mount: special device /dev/hdd does not exist.

The contents of /etc/fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=c1bc195b-022a-47ae-b9b0-d24d9ea2e73a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=86dcdff1-1130-4cc9-b8db-318d3491f677 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by alienexplorers on 2007-07-24
Why not add a line like:
> /dev/hde /media/cdrom1 udf,iso9660 user,noauto 0 0

---

### Post by deadlikeoscar on 2007-07-24
Do you have one or two DVD/CD drives?

If one, try changing /dev/hdd to /dev/cdrom in fstab.

---

### Post by DarkMana on 2007-07-24
I tried both of those, neither worked. The first suggestion caused a second drive ("CD-ROM 2") to appear in File Browser (as it seems it should have) although both of the drives gave the "Unable to mount..." error.

---

### Post by deadlikeoscar on 2007-07-24
What about changing it to /dev/scd0?

---

### Post by DarkMana on 2007-07-24
> **deadlikeoscar said:**
> What about changing it to /dev/scd0?

Same error. :(

---

### Post by deadlikeoscar on 2007-07-24
Not that it will help but just so I know, did you remove the second drive from fstab?

Also, did your CD/DVD EVER work under Ubuntu?

---

### Post by kyphi on 2007-07-24
A similar situation has just been solved on another thread and may apply here.

Go into the BIOS and check your optical drive settings, that is IDE or AHCI.

Unfortunately I cannot be more specific since I have no idea if you are using IDE or SATA drives.

---

### Post by DarkMana on 2007-07-24
> Not that it will help but just so I know, did you remove the second drive from fstab?
Yes.

> Also, did your CD/DVD EVER work under Ubuntu?
The only time it worked was when I used the Live CD to set it up.

Also, it's IDE.

---

### Post by deadlikeoscar on 2007-07-24
Do you know what kernel you are currently using? I have had stuff change when I have updated kernels. Mine used to be /dev/scd0 and then it became /dev/cdrom It was probably closer to yours when I first started using Ubuntu but I can't be sure. I was thinking that Ubuntu probably had an older kernel on the Live CD than the one you are using now. If it worked with the older kernel then I'm wondering what has changed.

---

### Post by DarkMana on 2007-07-24
I'm running Feisty Fawn 7.04.

In fact, this whole setup was only done a couple of days ago. I suddenly found myself with an extra PC, and I've always wanted to try out Linux.

---

### Post by ravenwere on 2007-07-25
Sorry complete newb here but..

Why is /dev/cdrom0 in fstab listed as cdrom1 in the file browser. I thought it would be cdrom0.

ie: /dev/hdc /media/cdrom0
    /dev/hdd /media/cdrom1

then these would equate to a hardware setup of Secondary ide master(hdc) and slave(hdd).

Sorry again --thinking out loud --- on paper . Dont want to get  you off topic.

regards and good luck
r

---

### Post by DarkMana on 2007-07-25
> **ravenwere said:**
> Why is /dev/cdrom0 in fstab listed as cdrom1 in the file browser. I thought it would be cdrom0.


Probably because, in programming, array indices begin at zero. Then in File Browser, it would show it as "CD-ROM 1" because it's the first drive (and labeling it as "CD-ROM 0" doesn't make sense).

---

### Post by Orochi on 2007-07-25
You can go into a terminal and type 'sudo fdisk -l' to get a list of all devices connected to the computer. Then you can see what the CDROM drive is (ie is it hdd or hdc or hde, etc).

---

### Post by tcrosby86 on 2007-07-27
Im having the exact same problem hers my code thing -

```
timmy@ubuntu-book:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris
timmy@ubuntu-book:~$ 
```

---

### Post by alienexplorers on 2007-07-28
My fstab looks like this:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /graphics       ext3    defaults        0       2
/dev/hdb2       /home           ext3    defaults        0       2
/dev/hdb5       none            swap    sw              0       0
/dev/hdb6       /data           ext3    defaults        0       0
/dev/hda1       /windows        vfat    iocharset=utf8,umask=000     0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1    udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy   vfat    rw,user,noauto  0       0

> terminator@terminator-desktop:~$ sudo fdisk -l

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    c  W95 FAT32 (LBA)
/dev/hda2            1276        3649    19069155    f  W95 Ext'd (LBA)
/dev/hda5            1276        2097     6602683+   b  W95 FAT32
/dev/hda6            2098        2873     6233188+   b  W95 FAT32
/dev/hda7            2874        3649     6233188+   b  W95 FAT32

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1284    10313698+  83  Linux
/dev/hdb2            1285        2566    10297665   83  Linux
/dev/hdb3            2567        3716     9237375   83  Linux
/dev/hdb4            3717        4865     9229342+   5  Extended
/dev/hdb5            4291        4865     4618687+  82  Linux swap / Solaris
/dev/hdb6            3717        4290     4610592   83  Linux

Partition table entries are not in disk order


---

