---
title: "problem mounting internal ide drive"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by kditty on 2006-06-13
ok so heres a long story made short, i tried to install dapper alongside xp and badger. i messed my partitions up on the drive that i was trying the install on, so i formatted xp. that was my c:\ drive and i also have an e:\ drive, 120gb seatgate ide.

i was hoping this drive isnt currupted, and i dont think it is because i never touched the e:\ drive with gparted, only c:\ so im wondering why i cant mount this drive. ive tried a couple steps and im willing to try anything because i have all of my music on this hard drive about 30GB worth.

the drive is recognized in systedm>administration>disks but it says enabled and i cant browse it. when i try to access, i get this error: You do not have the permissions necessary to view the contents of "disks-conf-hdd1".

---

### Post by givré on 2006-06-13
okay guy,
post here your /ets/fstab, your /etc/mtab
and the result of ```
sudo fdsisk -l
```

---

### Post by kditty on 2006-06-13
[QUOTE=givré]okay guy,
post here your /ets/fstab, your /etc/mtab
and the result of ```
sudo fdsisk -l
```[/QUOTE]

----fdisk results
kyle@kdapper:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19170   153982993+  83  Linux
/dev/hda2           19171       19452     2265165    5  Extended
/dev/hda5           19171       19452     2265133+  82  Linux swap / Solaris

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       14593   117218241    7  HPFS/NTFS



------fstab results
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd /media/windows ntfs umask=0222 0 0



-------mtab results
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-23-386/volatile tmpfs rw 0 0
/dev/hdd1 /tmp/disks-conf-hdd1 ntfs rw 0 0

---

### Post by anaconda on 2006-06-13
can you access it with root rights?

write to terminal 

sudo nautilus

and look to /tmp/disks-conf-hdd1  it seems to be mounted there.

Or if you prefer to do the same with terminal:
sudo su
cd /tmp/disks-conf-hdd1
ls -la

I think, that the last line in your fstab file should be
/dev/hdd1 /media/windows ntfs umask=0222 0 0

because hdd is the hard-disk, and hdd1 is the first partition of your hard-disk. And I think you want to mount the partition..
then after you reboot your hdd1 should be in /media/windows..

---

### Post by kditty on 2006-06-13
[QUOTE=anaconda]can you access it with root rights?

write to terminal 

sudo nautilus

and look to /tmp/disks-conf-hdd1  it seems to be mounted there.

Or if you prefer to do the same with terminal:
sudo su
cd /tmp/disks-conf-hdd1
ls -la

I think, that the last line in your fstab file should be
/dev/hdd1 /media/windows ntfs umask=0222 0 0

because hdd is the hard-disk, and hdd1 is the first partition of your hard-disk. And I think you want to mount the partition..
then after you reboot your hdd1 should be in /media/windows..[/QUOTE]


yea that worked man, thanks alot guys.

---

