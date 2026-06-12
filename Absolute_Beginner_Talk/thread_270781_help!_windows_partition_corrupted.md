---
title: "help! windows partition corrupted?"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by terrymcintyreatyahoo.com on 2006-10-03
I installed Ubuntu 6.06 LTS on an HP a1250n. When I tried booting to Windows, got HP's magickal recovery partition, which offered to wipe the real Windows partition with a virgin install of Windows ... a scary prospect! Tweaked menu.lst to point to the 2nd partition, and it failed to boot Windows; the partition checksum was incorrect, iirc.
Tried to mount the disk within linux, that also failed. If there's any way to recover data from this partition ( it has hundreds of jpg files from my travels ), I could back up my photos and rebuild the partition.

Output of fdisk -l :

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 1046 8399128+ c W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 1047 17324 130753035 7 HPFS/NTFS
/dev/sda3 17325 30047 102197497+ 83 Linux
/dev/sda4 30048 30401 2843505 5 Extended
/dev/sda5 30048 30401 2843473+ 82 Linux swap/Solaris

Attempted to mount via:

mount -t ntfs /dev/sda2 /media/windows
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

dmesg output is:

[17182680.600000] NTFS-fs warning (device sda2): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17182680.600000] NTFS-fs error (device sda2): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17182680.600000] NTFS-fs error (device sda2): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17182680.600000] NTFS-fs error (device sda2): ntfs_fill_super(): Not an NTFS volume.

My first priority is to recover the data on /dev/sda2 -- if I can boot as Windows, all the better.

I modified the menu.lst entry and attempted to boot, and it failed:

title Windows NT/2000/XP
root (hd0,1)
savedefault
makeactive
chainloader +1

Any advice would be greatly appreciated. Thanks!

---

### Post by b_martinez on 2006-10-03
> **terrymcintyreatyahoo.com said:**
> I installed Ubuntu 6.06 LTS on an HP a1250n. When I tried booting to Windows, got HP's magickal recovery partition, which offered to wipe the real Windows partition with a virgin install of Windows ... a scary prospect! Tweaked menu.lst to point to the 2nd partition, and it failed to boot Windows; the partition checksum was incorrect, iirc.
Tried to mount the disk within linux, that also failed. If there's any way to recover data from this partition ( it has hundreds of jpg files from my travels ), I could back up my photos and rebuild the partition.

Output of fdisk -l :

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 1046 8399128+ c W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 1047 17324 130753035 7 HPFS/NTFS
/dev/sda3 17325 30047 102197497+ 83 Linux
/dev/sda4 30048 30401 2843505 5 Extended
/dev/sda5 30048 30401 2843473+ 82 Linux swap/Solaris

Attempted to mount via:

mount -t ntfs /dev/sda2 /media/windows
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

dmesg output is:

[17182680.600000] NTFS-fs warning (device sda2): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17182680.600000] NTFS-fs error (device sda2): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17182680.600000] NTFS-fs error (device sda2): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17182680.600000] NTFS-fs error (device sda2): ntfs_fill_super(): Not an NTFS volume.

My first priority is to recover the data on /dev/sda2 -- if I can boot as Windows, all the better.

I modified the menu.lst entry and attempted to boot, and it failed:

title Windows NT/2000/XP
root (hd0,1)
savedefault
makeactive
chainloader +1

Any advice would be greatly appreciated. Thanks!

Can't help with the Windows booting, but you may try to recover the data with either 
a: an Ubuntu-Live cd
b: a Knoppix cd
c: any other Live Linux cd.

You may also want to follow this link
[http://www.bootdisk.com/](http://www.bootdisk.com/)
and try to d/l the Win XP boot disks to find out if they'll boot your install.
  However, before doing that, I'b use the Linux CD to copy the info to a USB drive. JIC, ya know?
hth
Bill

---

### Post by steve.horsley on 2006-10-03
Looks like you have discovered this bug:
[https://launchpad.net/malone/bugs/32529](https://launchpad.net/malone/bugs/32529)

I just spent 20 minutes writing you a long reply, but the stupid forum decided to time me out so instead of posting it, it gave me a page saying I wasn't logged in (and the text disappeared). Crap!

In summary, this bug moves the starting cylinder of the windows partition, even if you don't want to repartition anything at all - it's crap software. 

The NTFS filesystem is probably still intact if you can find the correct starting cylinder again. Someone (read the bug report) had me send him a file that showed him what was going wrong - that file might just contain details on the original start address I suppose. Failing that, I have heard of rescue CDs that can guess the correct partition boundaries sometimes, but can't remember names.

You can use this command to make a copy of your existing MBR so that you can replace it if any attempt to fix things makes things worse. Copy the file to a USB stick so you can use a live CD to replace it if needed:
**sudo dd if=/dev/sda of=BADBOOTSECTOR bs=512 count=1**
replace it with this command
**sudo dd if=BADBOOTSECTOR of=/dev/sda**

Good luck.

---

### Post by confused57 on 2006-10-03
Here's to mount your windows partition:
[http://doc.gwos.org/index.php/DapperGuide#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://doc.gwos.org/index.php/DapperGuide#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

or

[http://psychocats.net/ubuntu/mountwindow](http://psychocats.net/ubuntu/mountwindow)

You could also try rootnoverify (hd0,1), instead of root (hd0,1)...sometimes this works.

---

