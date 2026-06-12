---
title: "Simple hard disk stuff..."
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by Culito on 2006-05-29
Hello, first time Linux user here.  Installed last night without a problem!  I love it so far.
So here we go:
I have a second hard disk that is Fat32 from my old Windows system.  I intend to only have mp3's on it, so I really don't care how it's formatted, so long as I can use it for my music storage.
It shows up in "disks" as: /dev/hda1
Windows Virtual Fat.
But it doesn't show up in places/computer.  I'd rather not have it as a folder, but just have it show up as a drive.  Here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>
<dump>  <pass>
proc                     /proc                   proc         defaults 
0       0
/dev/hdb1            /                          ext3         defaults,errors=remount-ro
0       1
/dev/hdb5            none                   swap        sw              
0       0
/dev/hdc              /media/cdrom0   udf,iso9660 user,noauto     
0       0
/dev/hdd              /media/cdrom1   udf,iso9660 user,noauto     
0       0
/dev/fd0               /media/floppy0    auto    rw,user,noauto  
0       0

What should I change here?  Oh, and make fstab so it's not "read only"?

Thanks, everybody!

---

### Post by joshrobinson on 2006-05-29
try adding

/dev/hda1   /media/music  vfat  defaults,umask=0000  0 0

then use this commands in terminal

cd /media
sudo mkdir music
sudo mount /dev/hda1

it should mount automatically from now on

---

### Post by Culito on 2006-05-29
Awesome.  Used sudo gedit.  Works great!  Thanks.

---

### Post by joshrobinson on 2006-05-29
[QUOTE=Culito]Awesome.  Used sudo gedit.  Works great!  Thanks.[/QUOTE]

your welcome, glad you got it working :D

---

