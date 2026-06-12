---
title: "[SOLVED] Auto mount an extended partition"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by lmlypfan on 2007-09-14
SSIA

I am looking to mount an extended partition at boot.  The ubuntu guides are instructions for mounting windows partitions.  

I know I need to mount fstab

"fdisk -l"

 Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16677   133957971   83  Linux
/dev/sda2           60425       60801     3028252+   5  Extended
/dev/sda3           16678       60424   351397777+  83  Linux
/dev/sda5           60425       60801     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   c  W95 FAT32 (LBA)

Thanks

---

### Post by lmlypfan on 2007-09-14
SSIA

I am looking to mount an extended partition at boot. The ubuntu guides are instructions for mounting windows partitions.

I know I need to edit fstab

"fdisk -l"

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 16677 133957971 83 Linux
/dev/sda2 60425 60801 3028252+ 5 Extended
/dev/sda3 16678 60424 351397777+ 83 Linux
/dev/sda5 60425 60801 3028221 82 Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 9728 78140128+ c W95 FAT32 (LBA)

Thanks

---

### Post by alienexplorers on 2007-09-14
Please list your fstab file.

---

### Post by lmlypfan on 2007-09-14
Just figured it out.

Thanks anyway :)

---

