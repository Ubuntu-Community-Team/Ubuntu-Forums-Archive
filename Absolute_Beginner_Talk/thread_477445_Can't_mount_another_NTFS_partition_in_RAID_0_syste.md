---
title: "Can't mount another NTFS partition in RAID 0 system."
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by mimiba on 2007-06-18
Hi All:

I've installed Ubuntu 7.04 in a RAID 0 system with preinstalled Windows XP (Dual-boot).

the ourput of "fdisk /dev/mapper/nvidia_hbdhjhac -l" are as below:

```


                &#25152;&#29992;&#35037;&#32622; Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_hbdhjhac1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/mapper/nvidia_hbdhjhac2            2551       20022   140343840    f  W95 Ext'd (LBA)
/dev/mapper/nvidia_hbdhjhac5            7268       20022   102454506    7  HPFS/NTFS
/dev/mapper/nvidia_hbdhjhac6            2551        2673      987966   82  Linux swap / Solaris
/dev/mapper/nvidia_hbdhjhac7   *        2674        7267    36901273+  83  Linux

```

This is
/dev/mapper/nvidia_hbdhjhac1 -- Windows XP system (NTFS partition)
/dev/mapper/nvidia_hbdhjhac5 -- Some data created & saved in windows XP (NTFS partition)

/dev/mapper/nvidia_hbdhjhac6 -- Linux swap
/dev/mapper/nvidia_hbdhjhac7 -- Ubuntu root /

After installing the Ubuntu, I followed some guide found in the internet, 

mount /dev/mapper/nvidia_hbdhjhac1 to /media/Windows 
 
```
sudo mount -t ntfs-3g /dev/mapper/nvidia_hbdhjhac1 /media/Windows
```

add the partition in /etc/fstab
after reboot, I can read and write the partion without any problem.

But follows the problem, when I use the same method to mount /dev/mapper/nvidia_hbdhjhac5
It failed..........

system showed:
```
mount: wrong fs type, bad option, bad superblock on /dev/mapper/nvidia_hbdhjhac5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

the dmesg | tail showed:

```
[  202.420000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[  202.436000] NTFS-fs warning (device dm-2): is_boot_sector_ntfs(): Invalid boot sector checksum.
[  202.436000] NTFS-fs error (device dm-2): read_ntfs_boot_sector(): Primary boot sector is invalid.
[  202.436000] NTFS-fs error (device dm-2): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[  202.436000] NTFS-fs error (device dm-2): ntfs_fill_super(): Not an NTFS volume.

```

I don't know what's heppan, can anyone help me?

---

