---
title: "dual boot"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by everest on 2007-12-13
Hi all,
Can anyone solve this problem...I had windows installed on my home pc. It has a 40GB IDE harddisk and the motherboard has an inbuilt SCSI host adapter. I had partitioned it C(10GB) & D(10). Installed Windows XP on C drive and use D drive to store data. Now I installed Ubuntu on remaining free space, approx. 20 GB. Installation went smooth and I am able to boot into Ubuntu but I can't boot Windows for some reason. I played arround with the /boot/grub/menu.lst file, changed some settings but it wouldnt boot at all, all it says is starting windows on a black screen...
here is the output of fdisk -l command.
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        4865    23719972+   f  W95 Ext'd (LBA)
/dev/sda5            1913        3187    10241406    7  HPFS/NTFS
/dev/sda6            3249        4865    12988521   83  Linux
/dev/sda7            3188        3248      489951   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by PmDematagoda on 2007-12-13
Post the result of:-

```
cat /boot/grub/menu.lst
```

---

