---
title: "New to Linux, partition access problem"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by xt828 on 2006-07-16
I just installed Ubuntu 6.06, my first foray into the Linux world. My PC has three hdds, 2x80gb raided and 1x300gb.  The 80gb drives are split into 3 partitions, and the 300gb drive is in 4.  The only free partition I had at the time of install was the second partition of the 300gb drive.  Every partition other than the one Ubuntu is on are NTFS.  I've been trying to go through the walkthroughs on how to access NTFS partitions, but I'm not sure what I should be putting into my fstab.  

sudo fdisk -l give me this:
```
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9121    73264401    7  HPFS/NTFS
/dev/sda2           18243       27363    73264432+   7  HPFS/NTFS
/dev/sda3           27364       36483    73256400    7  HPFS/NTFS
/dev/sda4            9122       18242    73264432+   5  Extended
/dev/sda5   *        9122       17868    70260246   83  Linux
/dev/sda6           17869       18242     3004123+  82  Linux swap / Solaris

Partition table entries are not in disk order
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xffffca19 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sdb2            2612       19457   135315495    f  W95 Ext'd (LBA)
/dev/sdb5   ?      225433       75420   942511733+  b2  Unknown

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdc doesn't contain a valid partition table
```

I really don't have any idea what I'm doing here, I've been a Windows user my entire time using computers.  Any help would be greatly appreciated.

---

### Post by Jagot on 2006-07-16
Have you read this:

[https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html#id2532372](https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html#id2532372)

---

### Post by xt828 on 2006-07-16
I've run through that, and running the command "sudo mount -a" gives me this:
```

mount: /dev/sda1 already mounted or /media/disk1 busy
mount: according to mtab, /dev/sda1 is mounted on /tmp/disks-conf-sda1
mount: /dev/sda2 already mounted or /media/disk2 busy
mount: according to mtab, /dev/sda2 is mounted on /tmp/disks-conf-sda2
mount: /dev/sda3 already mounted or /media/disk3 busy
mount: according to mtab, /dev/sda3 is mounted on /tmp/disks-conf-sda3

```

Going to the places listed I can see the folders, but doubleclicking on them gives me the following error:
```

The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "disks-conf-sda1".

```

Any ideas?

---

