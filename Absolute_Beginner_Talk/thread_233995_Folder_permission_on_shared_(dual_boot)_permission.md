---
title: "Folder permission on shared (dual boot) permission"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by coffeejunkie on 2006-08-10
Hi,

I've got a problem with the permissions on the FAT-32 partition that I use to share files between Windows XP and Ubuntu.  Learning by doing... I guess I messed up the settings don't even quite know how.  

In the file browser it used to show a little lock icon on the folder but that's now gone.  What kind of permission should a folder like that have?  And who should be the owner?  For me it shows root but that can't be right? :confused: 

I tried changing it with chmod but that doesn't seem to have any effect.  Maybe because it's owned by root?

Would appreciate any help and promise that I'll remember it well...

Thanks!

---

### Post by djsroknrol on 2006-08-10
> **coffeejunkie said:**
> Hi,

I've got a problem with the permissions on the FAT-32 partition that I use to share files between Windows XP and Ubuntu.  Learning by doing... I guess I messed up the settings don't even quite know how.  

In the file browser it used to show a little lock icon on the folder but that's now gone.  What kind of permission should a folder like that have?  And who should be the owner?  For me it shows root but that can't be right? :confused: 

I tried changing it with chmod but that doesn't seem to have any effect.  Maybe because it's owned by root?

Would appreciate any help and promise that I'll remember it well...

Thanks!


When you used chmod on that file it did change..the lock symbol means it's owned by root...

1) Is Samba installed?
2) check system>adminstrative>Shared Folders for settings
3)Right click the file?folder and check permissions

---

### Post by coffeejunkie on 2006-08-10
> **djsroknrol said:**
> When you used chmod on that file it did change..the lock symbol means it's owned by root...

1) Is Samba installed?
2) check system>adminstrative>Shared Folders for settings
3)Right click the file?folder and check permissions

thanks for your help...

1) no Samba installed
2) Shared Folders doesn't show the directory that causes trouble.  I can't change the settings for that folder.
3) Right click on folder doesn't work, the permissions checkboxes are greyed out and not clickable.

It seems that the folder is still owned by root though, here's what I see in a terminal

drwxrwxrwx   7 root root  4096 1969-12-31 19:00 share

Thanks!!

---

### Post by Indras on 2006-08-10
FAT32 doesn't support Unix-style file permissions.

See my post here for info on how to change your FAT32 permissions:
[http://www.ubuntuforums.org/showthread.php?t=226255](http://www.ubuntuforums.org/showthread.php?t=226255)

---

### Post by djsroknrol on 2006-08-10
I have 3 HD's in my computer all containing fat32 partitions...I present my fstab for clarification:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1	vfat   ** rw**,uid=1000,gid=1003,auto        0       0
/dev/hdb1       /media/hdb1	vfat    rw,uid=1000,gid=1003,auto        0       0
/dev/hdc1       /media/hdc1	vfat    rw,uid=1000,gid=1003,auto        0       0
/dev/hda3       none            swap    sw	0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto	0       0


```

note the bold item. That "rw" gives read/write permissions..that's the easiest way I've found to get there, and it works like a charm. Theuid & gid numbers were put in thru

System>Administration>users and groups for the network and local users to be able to access the drives as well...

---

