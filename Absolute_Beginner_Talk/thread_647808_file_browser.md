---
title: "file browser"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by radradrobotanks on 2007-12-22
hello,

When I go places->computer which opens up a Windows like 'My Computer' showing cdrom, floppy, root, windows partition and the linux filesystem which are all in my fstab annoyingly it also shows another drive which is not in my fstab called XP nor is it mountable. How can i stop this drive from appearing? how does the file browser work out what partitions are available?

---

### Post by jken146 on 2007-12-22
The command ```
sudo fdisk -l
``` shows you what your partitions are.  If there's one that doesn't exist but is trying to be mounted anyway, take a look in /etc/fstab for a bogus entry.  If in doubt, just post the output of that command and the contents of that file here.

---

### Post by radradrobotanks on 2007-12-22
here is my fstab, all of the partitions bellow except proc and floppy (commented out) are listed in places->computer but there is a extra listing called xp which isnt in my fstab as you can see.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/lvmVolume-root
UUID=48b671f2-85ca-4c4f-ac15-c6eea9c41cd8 /               xfs     defaults        0       1
# /dev/mapper/via_baddjcdace5
UUID=92268427-729a-4380-b0d1-642e66810c8b /boot           ext3    defaults        0       2
# /dev/mapper/via_baddjcdace10
UUID=b8975b3d-2063-44ab-b430-61982cb796f9 none            swap    sw              0       0
# cdrom
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# no floppy atm
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
# windows
/dev/mapper/via_baddjcdace1 /media/windows ntfs  nls=utf8,umask=0000 0    0

---

### Post by jken146 on 2007-12-22
OK, try checking the entry in Computer.  It'll be a symbolic link to somewhere I guess.  Right-click > Properties might tell you where.  If that doesn't help, try looking in /media and /mnt for a folder called xp.

---

### Post by radradrobotanks on 2007-12-22
information from right clicking:

Label: XP
Size: 78.1 (correct size of my windows partition)
Media: Hard Disk
UUID: A00CF6900CF660A8
File System: ntfs 3.1

Mount Point: Not Mounted
File System: Not Mounted
Mount Option: Not Mounted

When i try and mount it it requires my password.

It then prompts saying "Cannot mount volume"
Unable to mount the volume 'XP'.

Details
fuse: mount failed: Device or resource busy FUSE
mount point creation failed Unmounting /dev/sda1 (XP)

I should probably have mentioned this before i am using dmraid to raid0 2 sata drives using my motherboards onboard fake raid sata controller.
Since it is a raid0 striped setup /dev/sda1 would be gibberish.

---

### Post by jken146 on 2007-12-22
Hmm, and you also have an icon in Computer for your windows partition, right?

edit:  yeah, that's what you said.  Well, I'm sorry but I don't think I can help you any more (stuck in Xubuntu at the mo, so I can't play around in Gnome myself).  See if there's an extra folder in /media and delete it if it's called xp.

Best of luck.

---

### Post by radradrobotanks on 2007-12-22
Yes I have managed to mount my windows partition by adding:
# windows
/dev/mapper/via_baddjcdace1 /media/windows ntfs nls=utf8,umask=0000 0 0  t
to fstab. This has placed a link on my desktop to my windows partition. I think i may have incorrectly tried to setup my windows partition when installing and that is what is being shown as XP.

No there is no extra folder in /media or /mnt

---

### Post by radradrobotanks on 2007-12-24
I just noticed that nautilus thinks that the unexpected drive is like a cdrom or floppy not a harddrive.

---

### Post by radradrobotanks on 2008-01-02
thanks 2 zarqoon here are instructions to hide non sense drives from nautilus


"Re: how does nautilus decide what drives/partitions to display?
It seems that some people had this kind of problem before
The solution is in post 34 in this thread
http://ubuntuforums.org/showthread.php?t=428196&page=4"

---

