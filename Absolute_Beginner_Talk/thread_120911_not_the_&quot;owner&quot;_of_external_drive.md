---
title: "not the &quot;owner&quot; of external drive?"
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by fcendejas on 2006-01-23
Hi all, just installed Ubuntu today, works well.  Only thing is I plug in my firewire drive, which reads fine, but i can't write to it.  Ubuntu says I'm not the "owner" of the drive, I also can't change the permissions?
I set it up so that I'm the only user.

-p

HP Pavilion laptop
breezy badger

---

### Post by aysiu on 2006-01-23
Sounds as if it's not mounting properly.

Two ways to handle this:

1. Modify your /etc/fstab file so that it will mount with the proper permissions.

2. Temporarily assume root privileges so you can read it.

Which do you want?

---

### Post by turbo63 on 2006-01-23
I'm with fcendejas on this.  I can't figure out how to write or modify to anything other than my desktop unless I long into Ubuntu as root.  And while I'm logged into gnome as root it won't let me change any owner info on the files either.  What do I need to do to my fstab to be able to modify my FAT32 partition?

---

### Post by Cysman on 2006-01-24
This might be the answer for me too.  Er eh....how do you modify the fstab to give the permission.  More or less, what do you type.  It's gotta be in crayon for me.

---

### Post by aysiu on 2006-01-24
[QUOTE=Cysman]Er eh....how do you modify the fstab to give the permission.  More or less, what do you type.  It's gotta be in crayon for me.[/QUOTE] See the fourth link of my signature.

The only difference: it's probably something like /dev/sda1 or /dev/sde1 instead of /dev/hda1. If your filesystem isn't NTFS or FAT32, let me know.

Otherwise, the link explains everything.

The terminal (where you type all the commands) is in Applications > Accessories > Terminal

---

### Post by fcendejas on 2006-01-24
Wondering, does this have anything to do with the fact that my external drive is NTFS?  Does Ubuntu have different reading/writing abilities on NTFS vs FAT32?

---

### Post by Cysman on 2006-01-24
I feel like such a lutz here but I read your link and started looking at it but a question, again, the instructions are for mounting windows.  Does this solve my problem with not having the right permissions for my cdrw?

---

### Post by aysiu on 2006-01-24
[QUOTE=fcendejas]Wondering, does this have anything to do with the fact that my external drive is NTFS?  Does Ubuntu have different reading/writing abilities on NTFS vs FAT32?[/QUOTE] NTFS is read-only. FAT32 is read/write. You should be able to at least *read* the NTFS partition if it's mounted correctly. You won't be able to modify files, though.

---

### Post by aysiu on 2006-01-24
[QUOTE=Cysman]I feel like such a lutz here but I read your link and started looking at it but a question, again, the instructions are for mounting windows.  Does this solve my problem with not having the right permissions for my cdrw?[/QUOTE] A CD-ROM drive is an entirely different thing, and, to be honest, I don't really know much about troubleshooting CD-R/DVD-R drives.

---

### Post by fcendejas on 2006-01-24
That solves my issue then - guess I'll never quite be able to write to it.  Maybe I'll have to make a partition on the external that is FAT32?  But it the permission problem was seperate, I imagine.

---

### Post by pek on 2006-05-06
i have a similar problem.

external firewire drive, xfs.

mounted correctly, dmseg doesn't complain about anithing wrong. i can read, buto write i have to be root :\

here is my fstab

```
 cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               xfs     defaults        0       1
/dev/sda1       /boot           ext2    defaults        0       2
/dev/sda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

and my mtab

```
 cat /etc/mtab
/dev/sda3 / xfs rw 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-21-k7/volatile tmpfs rw 0 0
/dev/sda1 /boot ext2 rw 0 0
/dev/sdb1 /media/ieee1394disk xfs rw,nosuid,nodev 0 0

```

---

