---
title: "Read a WinXp partiton on xubuntu dapper and edgy"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-20
I'm sorry to triple post but I ran into a strange error. I should also mention that I'm in xubuntu Edgy right now and plan on doing the same thing in my Dapper partition when I'm finished, and I hope that is not the problem.

first I perfectly followed these instructions from an earlier post about permission to read a media 1 partition, and it did not work:

**"This is what you do--paste (do not retype) these commands into the terminal:

Unmount the drive (it appears to be mounted now):
Code:

sudo umount /media/hda1

Edit the /etc/fstab while also making a backup copy:
Code:

sudo nano -B /etc/fstab

Change this line:
Code:

UUID=B444EE8344EE47A6 /media/hda1 ntfs defaults 0 0

to this line
Code:

UUID=B444EE8344EE47A6 /media/hda1 ntfs nls=utf8,umask=0222 0 0

Then save (Control-X, Y, Enter) and finally
Code:

sudo mount -a

to remount it. Should work now."**



-----Then it said this after crtl x, y, enter----:

:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/B444EE8344EE47A6,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so


----Then I tried to change it like this-----:


:~$ sudo umount /media/hda1
umount: /media/hda1: not mounted
me@me:~$ sudo nano -B /etc/fstab

and I tried this from another post:

 your fstab entry would be:

UUID=B444EE8344EE47A6 /media/hda1 ntfs umask=0222 0 0

Typing "sudo /dev/UUID=B444EE8344EE47A6 /media/hda1 ntfs defaults 0222 0 0" won't do much more than complain at you ... you'll need to update your /etc/fstab and remount any devices you change with mount -o remount /media/hda1 for example.


me@me:~$ sudo mount -o remount /media/hda1
mount: /media/hda1 not mounted already, or bad option
me@me:~$ sudo mount -o remount UUID=B444EE8344EE47A6 /media/hda1
mount: you must specify the filesystem type
me@me:~$ sudo mount -o remount UUID=B444EE8344EE47A6 /media/hda1 ntfs defaults,unmask=0222 0 0
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
me@me:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/B444EE8344EE47A6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

----I have saved these errors from terminal in case I really screwed things up.----

Thanks and sorry for posting about the same thing three times, it's just that I have the terminal opened right now with the errors from posts 1 and 2, and I would like to fix this.

I also never got any responses back from my earlier posts. Sorry, and thanks again for the help.

---

