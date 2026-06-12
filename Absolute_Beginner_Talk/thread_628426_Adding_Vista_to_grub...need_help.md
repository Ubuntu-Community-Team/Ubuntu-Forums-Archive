---
title: "Adding Vista to grub...need help"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Mosse on 2007-12-01
I have read a lot of threads on this, but still cant get it to work,
Thing is I had windows Vista installed on my IDE driver, I only got one ide and it was working fine, now I want to have Ubuntu on my second drive a SATA one, so I installed it at the begining of that drive and all went fine, But Now I cant get Grub to load my Vista, I have always used XP before and grub always added XP automatic to the boot list.

So I have tried to add Vista to the list but havent got it to work

here is what it looks like now in grub menu.lst
bottom lines:
```
## ## End Default Options ##

title         	Windows Vista 64bit
rootnoverify 	(hd1,0)
chainloader   	+1

title		Ubuntu 7.10 64bit
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f8d7d076-bbfc-4cf6-8ae0-181208e6449e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10 64bit, Safemode
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f8d7d076-bbfc-4cf6-8ae0-181208e6449e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet



### END DEBIAN AUTOMAGIC KERNELS LIST
```

But it seams like it isnt (hd1,0), because I cant get it to boot...

here is how fdisk -l looks like
```
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaca11cf7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20023   160834716    f  W95 Ext'd (LBA)
/dev/sda5               1        2550    20480000    7  HPFS/NTFS
/dev/sda6            2550        3826    10247168    6  FAT16
/dev/sda7            3826        7650    30716928    7  HPFS/NTFS
/dev/sda8            7651       20023    99386091    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2dcc2dcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1216     9767488+  83  Linux
/dev/sdb2            1291        8557    58366976    7  HPFS/NTFS
/dev/sdb3            8558       19457    87554250    f  W95 Ext'd (LBA)
/dev/sdb4            1217        1290      594405   82  Linux swap / Solaris
/dev/sdb5            8558       19457    87554218+   7  HPFS/NTFS

Partition table entries are not in disk order

```

But when I open the media folder in ubuntu it says that the vista parttion is called sdb5
so I tried (sd1,4) and couldnt boot... Also tried a lot of combinations (hd0,0) 1,0 0,1 etc

---

### Post by JayTee on 2007-12-01
Try this entry in your GRUB menu.lst file

title		Windows Vista/Longhorn (loader)
root		(hd1,4)
makeactive
chainloader	+1

---

### Post by Mosse on 2007-12-01
Error 12: Invalid device requested :(

Edit:
Seams like the disk manger cant decide what disk to have  as a and b
new fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2dcc2dcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1291        8557    58366976    7  HPFS/NTFS
/dev/sda3            8558       19457    87554250    f  W95 Ext'd (LBA)
/dev/sda4            1217        1290      594405   82  Linux swap / Solaris
/dev/sda5            8558       19457    87554218+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaca11cf7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20023   160834716    f  W95 Ext'd (LBA)
/dev/sdb5               1        2550    20480000    7  HPFS/NTFS
/dev/sdb6            2550        3826    10247168    6  FAT16
/dev/sdb7            3826        7650    30716928    7  HPFS/NTFS
/dev/sdb8            7651       20023    99386091    7  HPFS/NTFS

```

This seams to be more corrent also, since my Vista drive is mounted as sdb5 in ubuntu

---

### Post by meierfra on 2007-12-01
Since Vista is on  logical partition it might not be possible to get it to boot.

Could you explain the various "NTFS" and "Fat 16" partitions you have. Did you used to have another Windows OS on the  IDE drive ? Or do  you still have  a Windows OS on the Sata drive.

---

