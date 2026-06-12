---
title: "Raid0"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by LarsEriksson on 2006-06-08
I could not install ubuntu on my raid0-array, so i bought a new harddisk and installed it without any problem.
But now i want to get to my raid-array from ubuntu, i have searched the forums for a solution for hours, but i have not found anything that i can understand.

I have a nforce4-chipset for the array, and 2x250GB S-ATA drives.

Where should i start?

---

### Post by waster on 2006-06-08
You can't go from one disk to a RAID-0 array without a third disk, unless you reinstall from scratch. If you've got a third disk, you might as well do RAID5, which you can migrate to from one disk...

---

### Post by LarsEriksson on 2006-06-08
i think u misunderstood me ...

I have a raid-array consisting of 2x250GB S-ATA-drives on a nforce4 chip.
I have a third disk that has nothing to do with the raid, on this third disk i have installed ubuntu.
Now when i run ubuntu from my third(non raided) disk i want to be able to reach my raid0-array consisting of the other 2 disks.

:)

---

### Post by waster on 2006-06-09
[QUOTE=LarsEriksson]i think u misunderstood me ...

I have a raid-array consisting of 2x250GB S-ATA-drives on a nforce4 chip.
I have a third disk that has nothing to do with the raid, on this third disk i have installed ubuntu.
Now when i run ubuntu from my third(non raided) disk i want to be able to reach my raid0-array consisting of the other 2 disks.

:)[/QUOTE]

Ah, I see. nforce4 is a motherboard chipset, isn't it, not a RAID controller? Have you configured 'hardware RAID', i.e. set it up in the BIOS? If so, unless you have a proper server RAID card, look at: [https://wiki.ubuntu.com/FakeRaidHowto?highlight=%28hardware%29%7C%28raid%29](https://wiki.ubuntu.com/FakeRaidHowto?highlight=%28hardware%29%7C%28raid%29)

If it was an md, software RAID array, then you should be able to mount it with something like sudo mount /dev/md0 /mnt
and you can see the partitions with more /proc/partitions

If you have fake raid, you will see partitions which are part of the raid array, but these cannot be mounted on their own (certainly not if you have raid0).

---

### Post by LarsEriksson on 2006-06-09
Yes, the raid array works perfectly in windows.
Yes its a nforce4 soft-raid.

Ok, i think i got the raid activated or something now.

When i run fdisk -l i get the following:
```
x@x:/$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23564   189277798+  83  Linux
/dev/sda2           23565       24321     6080602+   5  Extended
/dev/sda5           23565       24321     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x0061 of partition table 5 will be corrected by w(rite)

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2        2611    20964825    f  W95 Ext'd (LBA)
/dev/sdc2   *        5223       60802   446446350    7  HPFS/NTFS
/dev/sdc5             418       37883   300941312   ff  BBT
x@x:/$
```

And as i have figured out /dev/sdc2 is the partition i want to mount.
Ive added the following line to fstab without any luck:

/dev/sdc2 /media/raid ntfs nls=utf8,umask=0222 0 0

---

### Post by Gorante on 2006-06-09
[quote=LarsEriksson]Yes, the raid array works perfectly in windows.
Yes its a nforce4 soft-raid.

Ok, i think i got the raid activated or something now.
[/quote]

How did you activated it?

I've your same problem (and configuration).
Raid isn't recognized and i see two different drives. I can Boot linux just switching the HDD boot priority in my mainboard BIOS settings.

---

### Post by LarsEriksson on 2006-06-10
I used Dmraid as posted in some guid i think, i cant really remember, i did alot of things and i dont really know what im doing :P

---

### Post by LarsEriksson on 2006-06-12
*bump*
Still cant get it working, anyone knows how i should do?
Oh yeah the filesystem is NTFS also.

---

### Post by zGhost on 2007-04-22
I have the exact same problem and im running 7.04 I get the error message 
Cannot mount volume 
Unable to mount the volume.
mount:wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or other error in some cases useful info is found in syslog - try dmesg|tail or so 
> [11337.421001] NTFS-fs error (device sdc1): ntfs_read_inode_mount(): Failed. Marking inode as bad.
[11337.421005] NTFS-fs error (device sdc1): ntfs_fill_super(): Failed to load essential metadata.
[12357.779456] NTFS-fs warning (device sdc1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[12357.816469] NTFS-fs error (device sdc1): ntfs_read_inode_mount(): $MFT/$DATA attribute not found. $MFT is corrupt. Run chkdsk.
[12357.816476] NTFS-fs error (device sdc1): ntfs_read_inode_mount(): Failed. Marking inode as bad.
[12357.816481] NTFS-fs error (device sdc1): ntfs_fill_super(): Failed to load essential metadata.
[12427.467868] NTFS-fs warning (device sdc1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[12427.478034] NTFS-fs error (device sdc1): ntfs_read_inode_mount(): $MFT/$DATA attribute not found. $MFT is corrupt. Run chkdsk.
[12427.478040] NTFS-fs error (device sdc1): ntfs_read_inode_mount(): Failed. Marking inode as bad.
[12427.478043] NTFS-fs error (device sdc1): ntfs_fill_super(): Failed to load essential metadata.

What do i do?? please help
sys specs
sata 320 gb ubuntu install 
2x320gb sata raid (aparantly its a software raid) 
nforce4 an8 sli motherboard with xp3200+
Help!
Thanks

---

