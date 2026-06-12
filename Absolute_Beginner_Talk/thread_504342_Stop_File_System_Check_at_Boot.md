---
title: "Stop File System Check at Boot"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by bme on 2007-07-19
I have done "tune2fs -i 0 /dev/sda2" twice already. Yet I still have this annoying "forced check" of the filesystem at bootup. How do I finally stop this? I am using a laptop and I dont want this check specially when mobile....

---

### Post by mcduck on 2007-07-19
> **bme said:**
> I have done "tune2fs -i 0 /dev/sda2" twice already. Yet I still have this annoying "forced check" of the filesystem at bootup. How do I finally stop this? I am using a laptop and I dont want this check specially when mobile....

Could you post here outputs of "sudo fdisk -l" and "cat /etc/fstab"?

---

### Post by bme on 2007-07-19
fdisk -l....

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7        1312    10485760   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1312        9469    65517568    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4            9469        9730     2097152    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5            9469        9730     2096128   dd  Unknown

cat /etc/fstab.....

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=eb1c5f41-bdbe-4ecb-9d15-151c416390f0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D7-0405  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=B2F0962AF095F537 /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=E242-9809  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by mcduck on 2007-07-19
> **bme said:**
> fdisk -l....

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7        1312    10485760   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1312        9469    65517568    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4            9469        9730     2097152    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5            9469        9730     2096128   dd  Unknown

cat /etc/fstab.....

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=eb1c5f41-bdbe-4ecb-9d15-151c416390f0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D7-0405  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=B2F0962AF095F537 /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=E242-9809  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Try editing your /etc/fstab to disable fsck on your vfat and ntfs partitions by changing their entry lines last number from 1 to 0. 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=eb1c5f41-bdbe-4ecb-9d15-151c416390f0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D7-0405  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda3
UUID=B2F0962AF095F537 /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/sda5
UUID=E242-9809  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Fsck on windows file systems is not much use, and having '1' on those partitons is wrong anyway. '1' Should only be used for root partiton, '2' for other partitons that you want to check and '0' to disable fsck on that partition.

---

### Post by bme on 2007-07-19
I'll try that...Thanks a lot...

---

### Post by s_telios on 2007-07-20
It worked for me.
Booting was taking ages before. \\:D/

---

### Post by freesitebuilder on 2007-07-21
I've tried this, as XP disk check held up boot as there always seem to be errors. :(  This is what I have now:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=e27c3bdd-f406-4b36-bce0-43194b8f60d6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb3
UUID=fc54f5d1-d567-4ef2-ab68-9bf356d1facd /home           ext3    defaults        0       2
# /dev/hda3
UUID=ACA6-45C0  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=CCE9-0485  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
# UUID=7e37592d-06d7-4dfd-bc27-2d507385d7df /media/hda6     ext3    defaults        0       2
# /dev/hda8
# UUID=d604cebf-6454-4408-8e62-36eb79fe84bb /media/hda8     ext3    defaults        0       2
# /dev/hda7
# UUID=1906c7b3-5404-4007-b673-cb047aa688db none            swap    sw              0       0
# /dev/hdb2
UUID=9bc9d7f8-c39b-4915-9802-fa3665f71fe5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


But when I boot, I don't get any of the pre-GUI messages now - it goes straight to the Ubuntu "loading" page and the desktop. So I've obviously got something wrong - I only want to cut out the disk checks of the Windows partitions.

---

### Post by cryptoD on 2007-09-11
thanks for the tip man , its working fine

---

### Post by ZERO_SHIFT on 2007-11-05
Thanks a lot, this is so annoying :-)

---

