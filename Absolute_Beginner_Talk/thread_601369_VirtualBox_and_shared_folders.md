---
title: "VirtualBox and shared folders"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Talkie_Toaster on 2007-11-03
Hi, I recently installed Ubuntu 7.10 in Virtualbox. My host OS is Windows XP (Not my fault :P). I'd really like to share My Documents from XP to Ubuntu. I've installed the Guest Additions, and used the graphical interface to select the path and name the folder "MyDocuments", but whenever I type the code supplied in the documentation (sudo mount -t vboxsf [-o options] MyDocuments /home/drew/) into the terminal, I get:
```
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
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
```

Any help would be much appreciated.

---

### Post by tchoklat on 2007-11-03
It is telling you that your syntax in the command is wrong. you have typed it wrong. Check it again and retry.

---

