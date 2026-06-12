---
title: "Auto mount 'hda5' with fstab in dapper trouble"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by phil54601 on 2007-02-13
Hello;
Still having some trouble setting up fstab to auto mount a couple drives, the hda5 partition and fd0 as /media/floppy.
The floppy line from fstab is:
/dev/fd0	/media/floppy   ext2		defaults,uid=1000,gid=1000       0       0

This is what I've tried for hda5 in fstab:
#/dev/hda5  /home/phil/Linux2 	ext3 	defaults,uid=1000,gid=1000		0       0
#/dev/hda5  /home/phil/Linux2 	ext3 	auto,uid=1000,gid=1000,umask=0000	0       0
/dev/hda5  /home/phil/Linux2 	ext3 	defaults,uid=1000,gid=1000,umask=0666	0       0

In a terminal I get this error:
phil@phil-T23:~$ sudo mount -a 
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The fd0 line is commented out,but when I try it.  I get the same message just referencing fd0 instead.

In addition how can I mount these drives WITHOUT 'execute' permissions enabled?  I've tried umask=0666 for this.
Thanks
Phil

---

### Post by taurus on 2007-02-13
Is /dev/hda5 an ext3 filesystem?

```
sudo fdisk -l
```

---

### Post by phil54601 on 2007-02-13
Hello;
No,it is ext2.  That is part of the problem.  Do I need to reboot or just save fstab & in a terminal do:
 phil@phil-T23:~$ sudo mount -a
Thanks

---

### Post by steve.horsley on 2007-02-13
This should help
[http://www.troubleshooters.com/linux/ext2toext3.htm](http://www.troubleshooters.com/linux/ext2toext3.htm)

Similarly with the floppy: Are you sure it's ext2? Floppies are normally vfat. I seem to remember that 'auto' works nicely.

---

### Post by phil54601 on 2007-02-14
Hello;
The fd0 automount partly works for 'vfat'.  It auto-mounts, but Only 'root' can unmount it.
I have used both of these forms:
/dev/fd0	/media/floppy   vfat		auto,uid=1000,gid=1000       0       0
/dev/fd0	/media/floppy   vfat		defaults,uid=1000,gid=1000       0       0
with the same results.

For the hda5 partition--
sudo fdisk -l provides:  

Disk /dev/hda: 48.0 GB, 48004669440 bytes
240 heads, 63 sectors/track, 6201 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         538     4067248+  1b  Hidden W95 FAT32
/dev/hda2   *         539         809     2048760    b  W95 FAT32
/dev/hda3             810        2104     9790200   83  Linux
/dev/hda4            2105        6201    30973320    f  W95 Ext'd (LBA)
/dev/hda5            2165        3384     9223168+  83  Linux
/dev/hda6            3385        6201    21296488+   b  W95 FAT32
/dev/hda7            2105        2164      453537   82  Linux swap / Solaris
 
'Gparted' says :
/dev/hda5    ext2.
Ilooked at the link provided:
[http://www.troubleshooters.com/linux/ext2toext3.htm](http://www.troubleshooters.com/linux/ext2toext3.htm)
I don't see where it helps me, unless hda5 should be ext3 also?  

I am confused.  'Gparted' says that hda3 is ext3 and hda5 is ext2, but fdisk lists both of them as ID 83 Linux.  Doesn't fdisk give ext2 & ext3 different ID numbers?
Thanks for the help!
Phil

---

### Post by steve.horsley on 2007-02-15
To allow normal users to mount and unmount partitions (or floppies), add a **user** option like this:
**/dev/fd0	/media/floppy   vfat		user,uid=1000,gid=1000       0       0**


As for hda5, I kind of assumed that you wanted it to be ext3. The link I gave you shows how to convert ext2 filesystems to ext3. If you are happy to leave it as ext2, then change the fstab to say that it is ext2 and it will probably mount OK then.

Fdisk does not have a separate number for every Linux filesystem type. The partition table (that fdisk prints) only has one number (0x83) for all Linux filesystem types. The specific type is located at the start of the partition itself. Gparted must be reading the partition itself to determine the exact type.

---

### Post by phil54601 on 2007-02-16
Hello Steve;
Neither one works.  Here is my current fstab line for 'fd0':
/dev/fd0	/media/floppy   vfat		user,uid=1000,gid=1000       0       0
I also used 'auto' & 'defaults' instead of the 'user' for both fd0 & hda5.

I moved my mount points to '/mnt' from /home/phil/ (for hda & hdc) -- much easier to do 'tar.tgz' backups, since I forget to exclude stuff.  Here is the fstab line for 'hda5':
/dev/hda5  /mnt/Linux2 	ext2 	user,uid=1000,gid=1000,umask=0666	0       0

Does having the floppy write protected cause problems with mounting(other than read-only)?  Whether \hda5 is ext2 or ext3 isn't really imporant, but I DO want the most safe & secure system possible. I'm tired of w2k crashing & viruses,and reinstalling.  I'm ready to switch to Ubuntu.
 Is the ',umask=0666' a problem?  I want them mounted WITHOUT execute permissions.

How much of a restart do I need to do?  Just save the corrected fstab & in a terminal do a 'sudo mount -a' or do I need to completly reboot?  Without the reboot, only the vfat & ext3 partitions are mounting.
Thanks
Phil

---

### Post by phil54601 on 2007-02-17
Hello All;
Just a quick follow up.  I was thinking that there may actually be errors on hda5.  In the terminal running 'sudo mount -a' produces this error message:
phil@phil-T23:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I tried the 'dmesg | tail' in the terminal with these results:
phil@phil-T23:~$ dmesg | tail
[17179795.532000] ath0: no IPv6 routers present
[17180502.244000] cdrom: open failed.
[17180602.784000] cdrom: open failed.
[17181052.928000] FAT: bogus number of reserved sectors
[17181052.928000] VFS: Can't find a valid FAT filesystem on dev fd0.
[17181528.372000] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
[17181835.824000] cdrom: open failed.
[17181852.276000] cdrom: open failed.
[17183097.140000] EXT3-fs: Unrecognized mount option "uid=1000" or missing value
[17183241.328000] EXT3-fs: Unrecognized mount option "uid=1000" or missing value

The bottom 2 lines appear to apply here.  There was no cd-rom inserted, the fd0 contained a boot disk with ext2 not vfat.  
Hda5 was empty, so I recently ran this command in a terminal:
sudo mkfs.ext3 -cv /dev/hda5
Under 'system > Administration > Disks' , when I select partition 'hda5' the correct mount point is listed but clicking 'Enable' just blinks!

Again, this is the current fstab line for hda5:
/dev/hda5  /mnt/Linux2 	ext3 	auto,user,uid=1000,gid=1000		0       0
Thanks
Phil

---

### Post by phil54601 on 2007-02-21
Hello All;
Just in case some one else is following this thread I solved the problem.  cfdisk reported that partition hda7 & hda5 overlapped.  The disk geometry was:
hda1 win2000
hda2 win98
hda3 Ubuntu root
hda4 extended
hda7 linux swap
hda5 ext2 then ext3 8.8 GB (problems)
hda6 fat32 windows linux pass between drive.
I deleted ALL the partitions in the extended partition, then recreated this:
hda5 linux swap
hda6 ext3 linux space 8.8 GB
hda7 fat32 (windows & linux pass through)
This line would still NOT mount the 8.8GB drive hda6:
/dev/hda6 /mnt/Linux2 ext3 defaults,uid=1000,gid=1000 0 0

However this line does make it possible to mount the 8.8GB partition:
/dev/hda6  /mnt/Linux2 	ext3	defaults		0       0

sudo mount -a
didn't mount it, but system>>Administration>>Disks did allow me to mount it on /mnt/Linux2.
I then in a terminal 'sudo nautilus'  I set owner/group to 'phil'
Thanks all for the help
Phil

---

