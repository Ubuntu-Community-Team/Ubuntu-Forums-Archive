---
title: "sorry if this sounds thick"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by liamhome on 2006-08-10
i have some mp3s i want to play on Ubuntu.
how do i find them?????
they are on drive D and Ubuntu is on E
and can't seem to find drive C (xp) or D (where i store my mp3s)
help please....sorry if im sounding a bit thick 
Liam

:confused:

---

### Post by xpod on 2006-08-10
I reckon you need to "mount" any other filesystems before you can use them.

It`s a case of creating a mount point in /media/ or somewhere similar like /mnt/ then you have to change your fstab to include the new devices you want to mount.

Unfortunately im still learning myself so wont risk giving you the commands to do this....just in case
Simple stuff though...someone will hhelp or you can just look through thr threads for similar mounting issues

Ps ..depending wether your xp is fat32 OR ntfs might be a separate issue as far as i know

---

### Post by givré on 2006-08-10
To know all the partition of your system (name are different in linux):
```
sudo fdisk -l
```
To know which partition are actually mounted (don't edit this file !):
```
more /etc/mtab
```
To know which partition are mount at boot time : 
```
sudo more /etc/fstab
```

You will have to change /etc/fstab so you mount all partition you want at boot time. A good howto for that : [http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)
If you are not happy with it, come back :cool:

---

### Post by Optiker on 2006-08-10
Here's a great reference that helped me with the same kind of problem...

[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

You need to mount your drives that contain the files in order to be able to access them. There are several considerations:

mount manually or automatically on boot
allow all users to read write or limit
FAT or NTFS file system on the drive you want to mount

The reference above walks you through those combinations. But first, you need to make those decisions. If you just want to read the drive, then doesn't matter if NTFS or FAT. If you want to write to it, then there's a complication in that writing to NTFS from Linux is possible, but most places I've read, not advised since there are still issues with reliability.

I formatted my Windows data drive as FAT specifically so I could write to it from Linux. My Windows C-drive is NTFS since I didn' anticipate writing to it. I automatically mount my Windows drives on boot so they are accessible without having to interrupt what I'm doing to mount them when I need them.

You'll want to list the partition tables, and there is a link in the sections referenced that takes you to the section on listing your partitions. This will let you see the naming of the partitions. You'll need that to edit the fstab file in Linux. You may need to create "mount points". These are just folders that will be the location of the drives you mount. I think that these are usually in the /media/ Linux folder. I've named my two Windows drives WinC and WinD just for my own preference.

The file you'll need to edit in Linux is /etc/fstab. Mine looks like this...
======================================
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user     0       0

=================================
My Windiws C-drive is sda1 and my Windows D-drive is sda5. sdb1 is an external USB hard drive that I keep connected for Windows backup.

NOTE: There is a blank line at the bottom. At one point when I was just beginning to set up, I inadvertently left it out and things didn't work. Be sure to leave the blank line in.

I'm not a very experienced Linux user, so for all I know, I may have something wrong in my fstab, but it seems to work.

Good luck!
Optiker

---

