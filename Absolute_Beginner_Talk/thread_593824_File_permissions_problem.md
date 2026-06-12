---
title: "File permissions problem"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by mezcla on 2007-10-27
I am having trouble accessing, copying, and deleting files on my usb flash drive.  When I check properties it says I am the owner of the folder and that I have read and write access.  If I right click files the "Move to trash" option is greyed out.  If I do "sudo rm filename" in a Terminal it tells me that it's a read only directory.  What do I need to do to sort this out?

I am running Gusty 64-bit.

---

### Post by taurus on 2007-10-27
What filesystem is that USB drive?

```
sudo fdisk -l
```

---

### Post by mezcla on 2007-10-27
Oh thanks I meant to include that.  It is vfat.  I have two flash drives and they are both giving me the same issues.

---

### Post by taurus on 2007-10-27
How do you mount them?  Do you mount them by hand or do they get automounted when you plug them in?

post the outputs of these two commands from a terminal.

```
mount
ls -la /media
```

---

### Post by mezcla on 2007-10-27
They are automounted when I plug them in.  Thanks for the help, btw.  

```
~$ mount
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda5 on /home type ext3 (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /media/sda2 type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=yason)
/dev/sdb1 on /media/WD USB 2 type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

:~$ ls -la /media
total 58
drwxr-xr-x  6 root  root     4096 2007-10-27 13:57 .
drwxr-xr-x 22 root  root     4096 2007-10-22 18:40 ..
lrwxrwxrwx  1 root  root        6 2007-09-03 00:35 cdrom -> cdrom0
dr-xr-xr-x  2 root  root     2048 2007-10-26 22:57 cdrom0
-rw-r--r--  1 root  root      104 2007-10-27 13:57 .hal-mtab
-rw-------  1 root  root        0 2007-10-23 18:20 .hal-mtab-lock
drwxrwx---  1 root  plugdev  8192 2007-10-22 18:40 sda1
drwxrwx--- 11 root  plugdev  4096 1969-12-31 19:00 sda2
drwx------ 13 yason root    32768 1969-12-31 19:00 WD USB 2

```

---

### Post by taurus on 2007-10-27
Are we talking about /dev/sdb1 (/media/WD USB 2) right?  What is the name of the file that you want to remove from "/media/WD USB 2"?

```
ls -la "/media/WD USB 2"
```

---

### Post by mezcla on 2007-10-27
Hey, I've figured it out.  It wasn't WD USB 2; the pen drive wasn't even mounted.  They were being automounted before in Dapper/Feisty and when I upgraded to Gutsy last week I guess they are no longer automounted?  I just assumed that it was still automounted.  I guess it threw me off that I could navigate the directory and see the files but it wasn't mounted.

EDIT.  I still can't delete items or copy.  What I want to do is backup the contents of my USB disk to my internal HD.  Here is the command you asked for in your last post.

```
yason@yason-desktop:~$ ls -la "/media/disk"
total 852
drwx------    9 yason root  16384 1969-12-31 19:00 .
drwxr-xr-x    7 root  root   4096 2007-10-27 14:18 ..
drwx------ 4369 yason root 229376 2007-10-19 11:46 391999p1_files
drwx------    2 yason root   4096 2007-09-25 20:27 arte
-rwx------    1 yason root  21508 2007-06-07 16:19 .DS_Store
-rwx------    1 yason root 146704 2007-10-24 16:04 exlporatory.svg
-rwx------    1 yason root 226735 2007-10-24 16:01 exploratory.svg
drwx------    4 yason root   4096 2007-09-18 18:20 Firefox
drwx------    3 yason root   4096 2007-10-23 07:37 fotos
drwx------    4 yason root   4096 2007-10-02 20:46 School
-rwx------    1 yason root  95990 2007-10-18 11:40 screenshot-20070623@142054.png
-rwx------    1 yason root  91648 2007-09-28 11:59 tesis.doc
drwx------    2 yason root   4096 2007-06-07 16:19 .Trashes
-rwx------    1 yason root   4096 2007-06-07 16:19 ._.Trashes
drwx------    2 yason root   4096 2007-10-27 13:07 .Trash-yason

```

---

### Post by mezcla on 2007-10-27
bump

---

### Post by taurus on 2007-10-27
What file(s) do you want to delete from /media/disk?  

What was the command that you ran to copy files from /media/disk to your harddrive?

---

### Post by mezcla on 2007-10-27
Here is the command I am running:

```
sudo cp /media/disk/School/ /home/yason/Schoolbackup/
```

I didn't know if I should put an -r in there (to make it copy subfolders) but neither is working.  It just gives me an input/output error.

If I try to delete certain files (in this case, a directory named 391999p1_files) it won't let me delete it.
```
yason@yason-desktop:/media/disk$ rmdir 391999p1_files/
rmdir: 391999p1_files/: Read-only file system

```

Thanks again!

---

### Post by taurus on 2007-10-27
```
cp -R /media/disk/School/*  /home/yason/Schoolbackup/
```

```
rm -rf 391999p1_files
-or-
sudo rm -rf 391999p1_files
```

---

