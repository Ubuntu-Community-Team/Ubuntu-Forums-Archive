---
title: "Mount USB External HD"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by Sethalos on 2008-04-15
I have Ubuntu on my laptop...and I have a Desktop that has Windows XP on it.  Now connected to my Desktop is my USB Ext HD with all my MP3's on it.

Now, I'd like to mount the share so that I can use Amarok to listen to my MP3's, but I'm having a heck of a time doing so.

The command I'm using is:

sudo mount -t smbfs //SETHALOS-DESKTO/USB-HDD (I)/MUSIC


I'm not to sure about the usb-hdd (i) but that's the path it shows me when I navigate to it via Ubuntu.

Ok, and the error I'm getting is:

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


I've looked at other posts but nothing seems to be working for me.

The actual path to my music directory looks like this: smb://sethalos-deskto/USB-HDD%20(I)/Music

So any help would be appreciated, I don't have a clue what I'm supposed to do here.

---

### Post by Inxsible on 2008-04-15
The one thing I notice, is that since there is a space in the path(between USB-HDD & (I) ), you will need to use quotes around it.

```
 sudo mount -t smbfs "//SETHALOS-DESKTO/USB-HDD (I)/MUSIC" 
``` of course the above would work provided the path you gave is correct. Shouldnt the Sethalos-deskto be sethalos-desktop?? unless that's just a typo

---

### Post by Sethalos on 2008-04-15
Hiya,

Thanks very much for the reply. I tried the command you placed in, and I actually get the same error as before.  Just a list of command information.

 sudo mount -t smbfs "//SETHALOS-DESKTO/USB-HDD (I)/MUSIC"

The only part i'm unsure of as far as the path goes is that when I navigate to it through Network, it shows up in the address bar as:

smb://sethalos-deskto/USB-HDD%20(I)/Music

I'm not sure if maybe I have the wrong syntax for the location.

---

### Post by Jiran on 2008-04-15
Inxsible has a good point, did you misspell "SETHALOS-DESKTOP"? You seem to be missing the 'P'.

---

### Post by Sethalos on 2008-04-15
Hi....I tried it both ways, and still manage to get the same error. Is there a way for me to find the exact path I need to use?

---

