---
title: "help with mounting external ipod &amp; drives??"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by myke on 2006-01-01
Howdy.  Everything including networking is finally working quite well for me with my recent switch to Ubuntu Breezy.  Only problem I'm having is somehow the mounting of external drives quite working about 12 hours ago and I don't know why.  Both my ipod and external cdrw drive will no longer mount and they were doing so perfectly before.  I tried using the terminal with the command 'sudo mount ipod' and it gives me this error:  can't find ipod in /etc/fstab or /etc/mtab

I'm not even sure my command was correct.  Any ideas about what might have caused this and how I migth fix it.  I could really use the help here folks as my external cdrw drive and ipod are used quite often!  

Thanks.

---

### Post by kaamos on 2006-01-01
Check if gnome-volume-manager is running. This is responsible for automounting devices.

---

### Post by sethmahoney on 2006-01-01
[QUOTE=myke]Howdy.  Everything including networking is finally working quite well for me with my recent switch to Ubuntu Breezy.  Only problem I'm having is somehow the mounting of external drives quite working about 12 hours ago and I don't know why.  Both my ipod and external cdrw drive will no longer mount and they were doing so perfectly before.  I tried using the terminal with the command 'sudo mount ipod' and it gives me this error:  can't find ipod in /etc/fstab or /etc/mtab

I'm not even sure my command was correct.  Any ideas about what might have caused this and how I migth fix it.  I could really use the help here folks as my external cdrw drive and ipod are used quite often!  

Thanks.[/QUOTE]

It sounds like you no longer have an ipod line in fstab.  Type

sudo gedit /etc/fstab

in a terminal.  You want to have a line that looks like this:

/dev/sde2	/mnt/ipod	vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0

(except all on one line, and the /dev/sde2 part might be something else).  The external drive problem may be something similar.

---

### Post by myke on 2006-01-01
How do I check that?  Please forgive my ignorance btw ... this is all quite new to me (linux that is).

---

### Post by sethmahoney on 2006-01-01
[QUOTE=myke]How do I check that?  Please forgive my ignorance btw ... this is all quite new to me (linux that is).[/QUOTE]

Type

sudo gedit /etc/fstab

in a terminal.  To start a terminal, go to the Applications menu, then System, then Terminal.

---

### Post by myke on 2006-01-01
This is the output I get when typing in what is suggested:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0


Should I add a line in for the ipod equalling what you say should be there and then save under gedit?

---

### Post by qferret on 2006-01-01
yes, but go to System -> Administration -> Device manager first.
Find the entry for your iPod. Look for the block.device entry under advanced.
This will be the first parameter of the line you will add.

Go to the /mnt directory and see what your iPod's mount point is actually called.
This will be the 2nd param.

---

### Post by myke on 2006-01-01
i found the ipod under the device manager but don't see 'block.device' nor '/mnt'.   They're not there.  However, if I check under the 'disks manager', and the ipod is listed as '/dev/sda1' with the access path as 'nosuid,auto,nodev,rw,umask=077,gid=1000,uid=1000'.   Tell me where I need to put this in the fstab and I'll do so.  

Thanks for you quick help btw.

---

### Post by linuxted on 2006-01-01
[QUOTE=kaamos]Check if gnome-volume-manager is running. This is responsible for automounting devices.[/QUOTE]


The EXACT same thing just happened to me.  gnome-volume-manager is running I think:

$ gnome-volume-manager

** (gnome-volume-manager:10405): WARNING **: manager.c/2199: already running?


Just wanted to share my misery since this used to work for me too.

---

### Post by qferret on 2006-01-01
[QUOTE=sethmahoney]

/dev/sde2	/mnt/ipod	vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0

(except all on one line, and the /dev/sde2 part might be something else).  [/QUOTE]

/dev/sda1 instead of /dev/sde2  ;-)

Go to Places -> Computer -> Filesystem -> mnt and see what the mount point should be.

It may be iPod, or it may be sda1.
(/mnt/iPod or /mnt/sda1 for the second part of the line you are adding)

---

