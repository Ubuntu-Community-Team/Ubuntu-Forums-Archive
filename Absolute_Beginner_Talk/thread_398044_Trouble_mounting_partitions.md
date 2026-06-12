---
title: "Trouble mounting partitions"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by chroniker on 2007-03-31
I'm having trouble mounting FAT32 partitions that are on hdb.

> :~$ sudo fdisk -l
Password:

Disk /dev/hda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2385    19157481   83  Linux
/dev/hda2            2386        2491      851445    5  Extended
/dev/hda5            2386        2491      851413+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4629    37182411    b  W95 FAT32
/dev/hdb2            4630        9723    40917555    f  W95 Ext'd (LBA)
/dev/hdb5            4630        9723    40917523+   b  W95 FAT32



> :~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             18856292   3391980  14506440  19% /
varrun                  387784        84    387700   1% /var/run
varlock                 387784         0    387784   0% /var/lock
procbususb               10240       104     10136   2% /proc/bus/usb
udev                     10240       104     10136   2% /dev
devshm                  387784         0    387784   0% /dev/shm
lrm                     387784     17580    370204   5% /lib/modules/2.6.17-11-generic/volatile

I added these 3 lines to /etc/fstab

> /dev/hdb1	/mnt/windows1	vfat	defaults	0	0
/dev/hdb2	/mnt/windows2	vfat	defaults	0	0
/dev/hdb3	/mnt/windows3	vfat	defaults	0	0

When I went to mount I get this

> # mount /mnt/windows1
# mount /mnt/windows2
mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root...snip...# mount /mnt/windows3
mount: special device /dev/hdb3 does not exist


What am I doing wrong?

---

### Post by yabbadabbadont on 2007-03-31
> /dev/hdb1 * 1 4629 37182411 b W95 FAT32
/dev/hdb2 4630 9723 40917555 f W95 Ext'd (LBA)
/dev/hdb5 4630 9723 40917523+ b W95 FAT32

There is no hdb3 and hdb2 is an extended partition.  It cannot be mounted as it only exists to contain logical partitions.  You should only try to mount /dev/hdb1 and /dev/hdb5.

---

