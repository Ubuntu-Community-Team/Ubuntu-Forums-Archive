---
title: "Mount ext3 Partition"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-10-07
I have a partition that I would like to back up some things on. How can I mount the partition? When I go root nautalis and right click root it says that the partiton is not removable and that it cannot execute pmount. How can I easily mount it?

thanks for the help.

---

### Post by Ayman on 2006-10-07
Have you tried to mount it using the Disks utility? It's available at: System > Administration > Disks. I haven't actually tried it before, but I believe it will do the trick.

---

### Post by odinfromvalhalla on 2006-10-07
in terminal:
```
sudo su
mount /dev/<device_name_here i.e.:hda1,sda5, whatever> /mnt/

```

---

### Post by aysiu on 2006-10-07
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by gdoermann on 2007-09-03
aysiu,
I did all of what it said to do on that link but this is what I get back when use:
```
sudo mount -a
```

```

root@doermann-desktop:/# sudo mount -a
Failed to access '/dev/disk/by-uuid/F4704DDA704DA3E8': No such file or directory
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Failed to access '/dev/disk/by-uuid/12764C6FB54FDEF9': No such file or directory
Failed to access '/dev/disk/by-uuid/49D931C321379F44': No such file or directory
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/disk/by-uuid/A628B000B5AB7639 (Files)
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/disk/by-uuid/6074BCD574BCAEE2 (Family Videos)
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/disk/by-uuid/B00CA8290CA7E914 (Media)
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/disk/by-uuid/F61417EA1417AC9D (Backup)

```

Can anyone help? I can't figure out why I can't mount this ext3 partition!

---

