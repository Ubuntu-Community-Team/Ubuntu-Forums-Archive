---
title: "strang mount/partition errors on dapper"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by algebraist on 2006-09-12
Hi all. My first post!

Got my first linux convert--convinced a friend to switch from XP
to Ubuntu Dapper on his Compaq laptop. He likes it (not even dual-boot
-- cold turkey) but... Ubuntu won't recognize his external, Western
Digital 160GB drive. The drive was running under XP.

Usually, Ubuntu pmounts external USB and Firewire devices, and places an
icon on the desktop. No such luck.

Below are some things I tried (lots of error messages ahead!).

Thanks for any suggestions!

S/






1)(a)  sudo mount -t ntfs /dev/sda1 /media/windows

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

(b) dmesg | tail

[17408277.980000] NTFS-fs error (device sda1): read_ntfs_boot_sector():
Mount option errors=recover not used. Aborting without trying to recover.
[17408277.980000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an
NTFS volume.
[17408283.780000] FAT: bogus number of reserved sectors
[17408283.784000] VFS: Can't find a valid FAT filesystem on dev sda1.
[17408291.408000] autofs: called with bogus options
[17409216.444000] FAT: bogus number of reserved sectors
[17409216.444000] VFS: Can't find a valid FAT filesystem on dev sda1.
[17409288.632000] NTFS-fs error (device sda1): read_ntfs_boot_sector():
Primary boot sector is invalid.
[17409288.632000] NTFS-fs error (device sda1): read_ntfs_boot_sector():
Mount option errors=recover not used. Aborting without trying to recover.
[17409288.636000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an
NTFS volume.

(c)  sudo mount -t vfat /dev/sda1 /media/windows

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


(d) dmesg | tail

[17408283.780000] FAT: bogus number of reserved sectors
[17408283.784000] VFS: Can't find a valid FAT filesystem on dev sda1.
[17408291.408000] autofs: called with bogus options
[17409216.444000] FAT: bogus number of reserved sectors
[17409216.444000] VFS: Can't find a valid FAT filesystem on dev sda1.
[17409288.632000] NTFS-fs error (device sda1): read_ntfs_boot_sector():
Primary boot sector is invalid.
[17409288.632000] NTFS-fs error (device sda1): read_ntfs_boot_sector():
Mount option errors=recover not used. Aborting without trying to recover.
[17409288.636000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an
NTFS volume.
[17409406.944000] FAT: bogus number of reserved sectors
[17409406.948000] VFS: Can't find a valid FAT filesystem on dev sda1.




2) (a) fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       20672   156280288+   7  HPFS/NTFS


(b) fdisk /dev/sda1

Device contains neither a valid DOS partition table, nor Sun, SGI or OSF
disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.


The number of cylinders for this disk is set to 20671.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by
w(rite)




(c) cfdisk

                            cfdisk 2.12r

                          Disk Drive: /dev/sda
                   Size: 160041885696 bytes, 160.0 GB
          Heads: 240   Sectors per Track: 63   Cylinders: 20673

Name        Flags     Part Type  FS Type         [Label]        Size(MB)
 ---------------------------------------------------------------------------
   sda1                   Primary   NTFS                       160031.05
                          Pri/Log   Free Space                  7.75


(d)  sudo mount -t hpfs /dev/sda1 /media/windows

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

(e) dmesg | tail

[17409216.444000] FAT: bogus number of reserved sectors
[17409216.444000] VFS: Can't find a valid FAT filesystem on dev sda1.
[17409288.632000] NTFS-fs error (device sda1): read_ntfs_boot_sector():
Primary boot sector is invalid.
[17409288.632000] NTFS-fs error (device sda1): read_ntfs_boot_sector():
Mount option errors=recover not used. Aborting without trying to recover.
[17409288.636000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an
NTFS volume.
[17409406.944000] FAT: bogus number of reserved sectors
[17409406.948000] VFS: Can't find a valid FAT filesystem on dev sda1.
[17409507.432000] FAT: bogus number of reserved sectors
[17409507.432000] VFS: Can't find a valid FAT filesystem on dev sda1.
[17409821.444000] HPFS: Bad magic ... probably not HPFS

3) (a) gparted shows the partition as filesystem type: Unknown (with a
black border) and says the DiskLabelType is msdos

---

