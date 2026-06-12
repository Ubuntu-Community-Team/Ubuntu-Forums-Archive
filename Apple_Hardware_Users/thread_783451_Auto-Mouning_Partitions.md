---
title: "Auto-Mouning Partitions"
date: 2008-05-05
forum: Apple Hardware Users
---

### Post by deamon_knight on 2008-05-05
I have a Powerbook setup to dual boot Mac OSX & Hardy. I want to be able to access the OSX partition from Ubuntu, so edited my Fstab to automount the partition and enabled HFS Kernel modules, and disabled journaling on the Mac Filesystem. The Mac OS attaches to the FS properly in /mnt/macintosh. I'd prefer to have an Icon on the desktop to represent the Mac Partition, like when you connect a USB drive. How can I do this?

Here is my FSTAB

<CODE>
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=f5ca7e55-7cb1-4745-acd9-da094498d36c /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda5
UUID=6dce2b57-4c8b-424f-b15e-d0bdaefc1c38 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Mac OSX Partition
# /dev/hda4	/mnt/macintosh	hfsplus	user,auto	0	0

/dev/hda4	/media/macintosh	hfsplus	user,auto	0	0


</CODE>

---

### Post by cyberdork33 on 2008-05-05
I think that should put an icon on your desktop... I mount a samba share on boot much the same way and get an icon on the desktop.

---

### Post by deamon_knight on 2008-05-06
Yea, Thats what I thought too. Unfortunately it doesn't. Any suggestions?

---

### Post by Jammy4041 on 2008-05-08
Does it have an icon in the Xubuntu equivalent of Places? Sorry- I haven't used Xubuntu much.

If there is try dragging the Hard Drive Icon-For your mac onto the desktop.

Maybe this will work.

---

### Post by deamon_knight on 2008-05-08
Sure, there is a cabinet with file systems. It properly shows the file system, the home folder and automounted filesystems like flash disks, but no Mac Partition. The Mac Partition is still a folder with the mount directory. Can anyone tell me how ubuntu identifies whats a folder and whats a separate partition?

---

