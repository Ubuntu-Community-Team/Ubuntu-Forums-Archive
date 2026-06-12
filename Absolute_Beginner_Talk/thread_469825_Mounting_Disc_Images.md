---
title: "Mounting Disc Images"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Cullen on 2007-06-10
I have googled, and tried everything mentioned.

I tried this
> 
sudo mount -o loop /path/to/file.iso /path/to/mount/point

and in response I get

> 
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


I have tried compiling CDEMU, I don't even know where to start on what went wrong there.

I have tried utilizing Acetone, and I have it where it will start without throwing any errors, but when I try to mount an image it says "Image was not mounted." and makes a breaking glass noise.

I am not this stupid.  What am I doing wrong?

---

### Post by MenZa on 2007-06-10
I'm curious; have you created the directory you're trying to mount the image to?

---

### Post by taurus on 2007-06-10
Try

```
sudo mount -t iso9660 -o loop /path/to/file.iso /path/to/mount/point
```

---

### Post by Cullen on 2007-06-10
Yes I have created the directory to mount to.

Tried ```
sudo mount -t iso9660 -o loop /path/to/file.iso /path/to/mount/point
```

Get ```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by taurus on 2007-06-10
Are you sure the file is an iso format?

---

### Post by Cullen on 2007-06-10
I have tried it on several ISO's including one that I created.

---

### Post by pistcivet on 2007-06-10
Maybe the kernel module isn't loaded. Try:
```
sudo lsmod | grep loop
```
If you get no output do:
```
sudo modprobe loop
```
and try mounting the .ISO again.

---

### Post by Cullen on 2007-06-10
I didn;t try the last thing posted, but I did solve my problem.

I uninstalled all the crap I had already put, Acetone, Fuseiso, etc... (Using synaptic)
Then I installed GMount, it works great, although it's in a foreign language.

---

