---
title: "How to mount iso files?"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by vaazu on 2006-08-09
Hi
I tried to mount my iso file following the instructions for ubuntu but I think it was for another desktop enviroment. I want to know how to mount iso files in xfce?

---

### Post by aktiwers on 2006-08-09
> **vaazu said:**
> Hi
I tried to mount my iso file following the instructions for ubuntu but I think it was for another desktop enviroment. I want to know how to mount iso files in xfce?

Im not sure, but try this:

```
sudo mount -o loop -t iso9660 /wherever/iso/image/is/image.iso /media/iso/ 
```

tell me if it works or not.. im not home and are typing this from a XP computer, so I cant test it.

---

### Post by vision on 2006-08-09
I think this will help - [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20CD-IMAGES](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20CD-IMAGES)

---

### Post by vaazu on 2006-08-09
The first one didnt work it gave me Usage: 
mount -V                 : print version
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

---

### Post by vaazu on 2006-08-10
anybody? I reale need to mount some iso files.

---

### Post by taurus on 2006-08-10
You mean this doesn't work at all?

```

sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop <filename>.iso /mnt/iso
(-o is letter o, NOT number 0!!!)

```

---

### Post by Brunellus on 2006-08-10
first you need to make a directory somewhere in your filesystem that you can mount that image to.  Doesn't have to be anything special, but just a directory.

so say I want to mount foo.iso that's in /home/brunellus .  First thing I need to do is make a place to mount it:

mkdir /home/brunellus/bar

then I'll mount my image

mount -o loop -t iso9660 /home/brunellus/foo.iso /home/brunellus/bar

the image should mount, then I can look in the newly-mounted filesytem by navigating to the directory to which I mounted the image

cd /home/brunellus/bar

---

### Post by vaazu on 2006-08-11
It just says
```
vahur@vahur-desktop:~$ sudo mount -t iso9660 -o loop /home/vahur/download/Linux Basic Introductory Level/Linux Basic Introductory Level CD1.iso /mnt/iso/
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

```

---

### Post by GoldBuggie on 2006-08-11
from what I see I would guess it is the spaces used in your path and file name
did you type them by hand instead of using TAB-completion??

Instead of " " write "\ " so ```
"/Linux Basic Introductory Level/"
``` would become ```
"/Linux\ Basic\ Introductory\ Level/"
```

---

### Post by vaazu on 2006-08-11
Thanks alot it worked :)

---

