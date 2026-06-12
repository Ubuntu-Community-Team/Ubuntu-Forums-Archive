---
title: "mounting partition, what am I doing wrong"
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by bim54 on 2005-08-04
I thought I followed these instructions:

[http://www.ubuntuguide.org/#mountunmountfat](http://www.ubuntuguide.org/#mountunmountfat)

but I must be doing something wrong.  The /media/windows is there.  When did the rest of the procedure, something isn't working.  I'm pretty new to Linux.  Here is a copy-paste from the Konsole thus for and that's where it's at now.  I have two hard drives, and I want to be able to access the second hard drive that has the FAT32 on it, I believe that's the hdb
Thanks in advance...more questions later I'm sure.


Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9796    78686338+   7  HPFS/NTFS
/dev/hda2            9797       14733    39656452+  83  Linux
/dev/hda3           14734       14946     1710922+   5  Extended
/dev/hda5           14734       14946     1710891   82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4111    33021576    c  W95 FAT32 (LBA)
charlie@dadslinux:~$  sudo mount /dev/hdb /media/windows/ -t vfat -o iocharset=ut f8,umask=000
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
charlie@dadslinux:~$

---

### Post by Ampersand on 2005-08-04
The order of the command is important, try "sudo mount -t vfat -o iocharset=ut /dev/hdb1 /media/windows/"

Richard

---

### Post by Buffalo Soldier on 2005-08-04
Could this be the problem? **ut f8**
```
charlie@dadslinux:~$sudo mount /dev/hdb /media/windows/ -t vfat -o iocharset=**ut f8**,umask=000
                                                                               ^
```

Have you tried **utf8**?
```
charlie@dadslinux:~$sudo mount /dev/hdb /media/windows/ -t vfat -o iocharset=**utf8**,umask=000
```

---

### Post by bim54 on 2005-08-04
This is what I get.

charlie@dadslinux:~$ sudo mount /dev/hdb /media/windows/ -t vfat -o iocharset=utf8,umask=000
Password:
mount: /dev/hdb already mounted or /media/windows/ busy
charlie@dadslinux:~$


I got this message when I tried it after reading the post.  I did a shut down and then restarted before the above.
If I look in the /media/windows it's empty.  I'm assuming that's where it should be.
Thanks

---

### Post by Ampersand on 2005-08-04
You might need to mount /dev/hdb1 instead of /dev/hdb. You can unmount drives using 'sudo umount /dev/hdb' (replacing /dev/hdb with whatever you need to unmount).

---

### Post by bim54 on 2005-08-04
That did it....Thanks everyone!!!!

I'm sure another question will be coming up soon enough.  This is starting to grow on me.

---

