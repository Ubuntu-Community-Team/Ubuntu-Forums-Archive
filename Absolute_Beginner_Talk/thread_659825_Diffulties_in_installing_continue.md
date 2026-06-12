---
title: "Diffulties in installing continue"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by zeca2k4 on 2008-01-06
Hi again, all

Well, after my first post regarding GRUB, I followed the advice given (THANKS!!) and managed to get GRUB to load, but it wouldn't allow UBUNTU or Windows to load.

Trying UBUNTU gets me CANNOT MOUNT DRIVE and WINDOWS goes into a spin, rebooting and rebooting.

So I had to FIXMBR to get to WINDOWS XP again.

My setup is: 
SATA1: Set for UBUNTO
SATA2: Set for DATA
SATA 3 and 4: RAID 0 with XP (I don't want to touch this AT ALL if possible)
SATA 5: Set for personal files

What do I have to do in order to get a DUAL-BOOT going?

I don't mind setting things in my BIOS as I've read, but I cannot set the SATA1 HD to boot from.  Is there something that needs to be done in order to be able to boot from it?

What other options can you guys see?

Thanks

---

### Post by blueridgedog on 2008-01-06
Can you boot on the live cd?

If so, post the output of:
```

sudo fdisk -lu
```

and 

```
mount
```

I would also like:

```
cat /proc/partitions
```

Ideally this will lead to instructions to be certain that grub is installed with the right root and to help in mounting the partition on sata1 (/dev/sda?) that contains your /boot/grub/menu.lst file and editing that file to boot your two operating systems.

---

### Post by Daveth on 2008-01-06
have you browsed this???

[https://help.ubuntu.com/community/FakeRaidHowto#head-6c76652aaaf5e147adaaca8b0547d2dd06f2c5ce](https://help.ubuntu.com/community/FakeRaidHowto#head-6c76652aaaf5e147adaaca8b0547d2dd06f2c5ce)

---

### Post by zeca2k4 on 2008-01-29
Hi again.  Been away, been busy, M$ has me bundled, all of which keep me from testing Linux .... arghhhh!!!

Anyway:

@Dave: yes I have, but that seems to be applicable when one wants to install onto a raid partition which is not my scenario. In any case, I will read it more thoroughly.

@blueridgdog:

here are the results of booting to LiveCD and performing the commands mentioned:
  --- sudo fdisk -lu

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3450fd80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78140159    39070048+  83  Linux
/dev/sda2        78140160   321669494   121764667+   f  W95 Ext'd (LBA)
/dev/sda5        99667323   321669494   111001086    b  W95 FAT32
/dev/sda6        78140286    99667259    10763487   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x15bba2c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   161597834    80798886    7  HPFS/NTFS
/dev/sdb2       161597835   321669494    80035830    f  W95 Ext'd (LBA)
/dev/sdb5       161597898   321669494    80035798+   7  HPFS/NTFS
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9e159e15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   204796619   102398278+   7  HPFS/NTFS
/dev/sdc2       204796620   321637364    58420372+   f  W95 Ext'd (LBA)
/dev/sdc5       204796620   221639627     8421504    0  Empty

Disk /dev/sdd: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00140000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1e8d74e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63   245344679   122672308+   7  HPFS/NTFS
/dev/sde2       245344680   488392064   121523692+   f  W95 Ext'd (LBA)
/dev/sde5       245344743   488392064   121523661    7  HPFS/NTFS

Disk /dev/sdf: 1039 MB, 1039663104 bytes
65 heads, 32 sectors/track, 976 cylinders, total 2030592 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *          32     2030591     1015280    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(991, 64, 32) logical=(976, 15, 32)

  ---mount

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sdf1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=999,utf8,umask=077,usefree)
/dev/sdb1 on /media/DRV3_VOL1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda1 on /media/disk-1 type ext3 (rw,nosuid,nodev)

   --- cat /proc/partitions
major minor  #blocks  name

   8     0  160836480 sda
   8     1   39070048 sda1
   8     2          1 sda2
   8     5  111001086 sda5
   8     6   10763487 sda6
   8    16  160836480 sdb
   8    17   80798886 sdb1
   8    18          1 sdb2
   8    21   80035798 sdb5
   8    32  160836480 sdc
   8    33  102398278 sdc1
   8    34          1 sdc2
   8    48  160836480 sdd
   8    64  244198584 sde
   8    65  122672308 sde1
   8    66          1 sde2
   8    69  121523661 sde5
   8    80    1015296 sdf
   8    81    1015280 sdf1
   7     0     661012 loop0

---

