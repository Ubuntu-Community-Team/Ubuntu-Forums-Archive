---
title: "Mount won't mount."
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by pinkpanther01010 on 2006-02-24
Alright well i'm trying to mount my hdb1 after having trouble with it working..and when I do

sudo mount /dev/hdb1 /home/ianownsyou/250

I get the error saying mount: /dev/hdb1 already mounted or /home/ianownsyou/250 busy

---

### Post by uopjohnson on 2006-02-24
There are a couple of things you should try:
```
sudo mount
```  will give you a listing of mounted file systems to see if /dev/hdb1 is already mounted.  You should also try creating a new dir and mounting there. 
```

mkdir /tmp/hd
mount /dev/hda1 /tmp/hd
```

---

### Post by pinkpanther01010 on 2006-02-24
When I type in sudo mount I get this - 

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)

And when I try to mount it to a diff. place I still get the mounted or busy error.

---

### Post by ecto on 2006-02-24
There are two possible causes to your problem
1) /dev/hdb was mounted at startup
2) /dev/hdb was not cleanly umounted when the system switched to runlevel0/6 from the last shutdown and last session you had the drive moutned.
The first thing you should try doing (if you have not already done so) is to try simply typing mount in terminal to check if the device is already mounted. Otherwise, proceed to do the followoing.
a)Open up a terminal
b)Type sudo sync
c)Type mount -o sync
d)Try mount /dev/hdb.
If this doesnt work repost.

---

### Post by pinkpanther01010 on 2006-02-24
ianownsyou@ianowns:~$ sudo sync
Password:
ianownsyou@ianowns:~$ mount -o sync
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
ianownsyou@ianowns:~$ sudo mount /dev/hdb
mount: can't find /dev/hdb in /etc/fstab or /etc/mtab

Still not working.

---

### Post by pinkpanther01010 on 2006-02-24
I also get a lot of Segmentation fault errors when opening programs, like from UT04 to even music players..meh

---

### Post by uopjohnson on 2006-02-24
[QUOTE=ecto]
d)Try mount /dev/hdb.
[/QUOTE]
should be 
```
sudo mount /dev/hdb /tmp/hd 

```
or wherever you are mounting to.
Also, are you sure you are trying to mount /dev/hdb1?  It looks like your primary drive is on scsi or sata(/dev/sda1)... hdb1 is the first partition of your primary slave on and IDE bus.  Is this the disk you are trying to mount?

---

### Post by pinkpanther01010 on 2006-02-24
Yeah, my primary drive is a SATA 74GB Raptor..Ubuntu is on that. What i'm trying to mount is a 250Gig IDE drive, and only IDE drive.

When trying your code, I still get the busy error.

---

### Post by Mustard on 2006-02-24
What's the output of ..

```
sudo fdisk -l
```

---

### Post by uopjohnson on 2006-02-24
well if it is the only ide drive it is probably on /dev/hda1 unless it is sharing the bus with the cd-rom.

---

### Post by pinkpanther01010 on 2006-02-25
The result of "sudo fdisk -l" is 

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8669    69633711   83  Linux
/dev/sda2            8670        9039     2972025    5  Extended
/dev/sda5            8670        9039     2971993+  82  Linux swap / Solaris

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3647    29294496    c  W95 FAT32 (LBA)


And I also have my cd-rom drive on the same IDE bus..

---

