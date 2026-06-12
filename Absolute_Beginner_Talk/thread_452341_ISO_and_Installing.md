---
title: "ISO and Installing"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by ayed on 2007-05-23
Ok, I have a ISO game which is supposed to work in XP. How do I install it in a an Ubuntu box? Wine or Qemu? 

Thanks.

---

### Post by lakersforce on 2007-05-23
This is already extensively documented at the Ubuntu [wiki.]("https://wiki.ubuntu.com/")

---

### Post by ayed on 2007-05-23
To no avail, I mean I know that to use Wine I need a .exe folder right? So what would the case be when I have an ISO folder the size of a 1.9 GB? Do I use Qemu instead? Please Help.

---

### Post by Terl on 2007-05-23
> **ayed said:**
> To no avail, I mean I know that to use Wine I need a .exe folder right? So what would the case be when I have an ISO folder the size of a 1.9 GB? Do I use Qemu instead? Please Help.

You can mount the iso; that will give you what you need to install it with wine.  From the wiki:  [Mounting an ISO]("https://wiki.ubuntu.com/MountIso?highlight=%28mount%29%7C%28iso%29")

---

### Post by ayed on 2007-05-30
I ran the first command and this is what I got:

ayed@ayed-desktop:~$ sudo mount -o loop -t iso9600 Battlefield 2.iso /home/ayed
Password:
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


What Happened, I can't see any file image? Then I ran the second command:

ayed@ayed-desktop:~$ sudo mount -o loop /path/to/cd/image.iso /cdrom
/path/to/cd/image.iso: No such file or directory


What Happened?

---

### Post by Outrunner on 2007-05-30
I think it's a bit more like 
```
sudo mkdir /media/iso
```
```
sudo mount -o loop -t iso9600 Battlefield\ 2.iso /media/iso
```

---

### Post by ayed on 2007-05-30
Got this:

ayed@ayed-desktop:~$ sudo mkdir /media/iso
ayed@ayed-desktop:~$ sudo mount -o loop -t iso9600 Battlefield\ 2.iso /media/iso
mount: unknown filesystem type 'iso9600'
mount: maybe you meant 'iso9660'?
ayed@ayed-desktop:~$ sudo mount -o loop -t iso9600 Battlefield 2.iso /media/iso
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ayed@ayed-desktop:~$ mount device
mount: can't find device in /etc/fstab or /etc/mtab

---

### Post by Outrunner on 2007-05-30
```
sudo mount -o loop -t iso9660 Battlefield\ 2.iso /media/iso
```

---

### Post by ayed on 2007-05-30
Thanks Man!

---

