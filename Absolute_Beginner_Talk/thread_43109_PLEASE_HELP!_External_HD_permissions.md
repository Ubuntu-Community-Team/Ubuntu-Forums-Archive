---
title: "PLEASE HELP! External HD permissions"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by xbilly on 2005-06-20
Okay. Here is the thing. I have three hard drives. One of to internals I use for Windows XP OS, The second internalI use for Ubuntu Linux, and a third is External and I use it as extra space when I am in windows.

NOW. I want to be able to use that external as a go between for Windows in Linux. I want to be able to read and write to it inlinux just as I do in windows. I have done the whole setting permissions thing and it says I am not the owner or that it is a read-only disk. 

I did some research, hit up the terminal and did the following/this is what I got:

root@billy:/home/billy # sudo fdisk -l /dev/hda

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS
/dev/hda2            9729        9729        8032+  83  Linux
root@billy:/home/billy # cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb        /media/usb0     auto    rw,user,noauto  0       0
root@billy:/home/billy # sudo cp /etc/fstab /etc/fstab.bak
root@billy:/home/billy # sudo gedit /etc/fstab

(gedit:16487): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
*** attempt to put segment in horiz list twice

My GEDIT file looks as such:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb        /media/usb0     auto    rw,user,noauto  0       0


This is where I am lost. 

I gather that hdb1 is my external and that I need to make it "dev/hda5 /media/windows32 vfat umask=000 0 0"??? However, I am not exactly sure since it days "errors=remount" and all that.

Is it because it is NTFS? I tried to reformat it in windows as FAT32, but the only option I had was NTFS for some reason. Please help?

billy

---

### Post by desdinova on 2005-06-20
Yep its because its NTFS. As MS have not released the specs for NTFS, writing to it is not recommended - plus, NTFS will not be able to understand the Linux permission system

---

### Post by TristanMike on 2005-06-20
[QUOTE=xbilly]I gather that hdb1 is my external [/QUOTE]
I Don't think this is correct, hdb1/hdb5 is your Ubuntu hard drive. 
hda# being you XP drive, which you can't see there, and hdb being the 2nd Physical drive (denoted by the "b" as opposed to the "a").  If I'm correct, the /dev/sdb /media/usb0 auto rw,user,noauto 0 0 would be your external, would it not?  Is it connected via usb.  If I'm completely misleading this guy then somebody smack me and clarify.....

TristanMike

---

