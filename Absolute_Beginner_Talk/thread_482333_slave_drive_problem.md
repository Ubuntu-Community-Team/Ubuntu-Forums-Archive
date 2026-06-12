---
title: "slave drive problem"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by guddr on 2007-06-23
I am using ubuntu 7.04 and I replaced my slave drive with another one.  I formatted it in etc3 using Gparted however it does not appear in my Home directory and I am unable to use it. The mountpoint is the same as the previous HD.  Thanks.

---

### Post by molly_001 on 2007-06-23
On the new physical drive, did you move the jumper to the appropriate position for slave? or maybe to cable select?

---

### Post by guddr on 2007-06-23
The jumper is set to slave and it shows that way in BIOS.

---

### Post by logos34 on 2007-06-23
> **guddr said:**
> I am using ubuntu 7.04 and I replaced my slave drive with another one.  I formatted it in etc3 using Gparted however it does not appear in my Home directory and I am unable to use it. The mountpoint is the same as the previous HD.  Thanks.

If Gparted recognized it correctly to able to format it, then it's not a jumper issue.  The mount point may be the same, but something else has changed...was the previous drive partition formatted ext3?  Also, UUID differences could be causing a problem. 

post the output from 

sudo fdisk -l

and 

cat /etc/fstab

---

### Post by guddr on 2007-06-23
The previous drive was formatted in NTFS.

---

### Post by ajgreeny on 2007-06-23
Then that will be at least part of the problem as fstab will still expect an ntfs file system.  I agree, however, that the UUID may also now be different and causing a problem for you.

---

### Post by guddr on 2007-06-23
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9636    77401138+  83  Linux
/dev/hda2            9637        9729      747022+   5  Extended
/dev/hda5            9637        9729      746991   82  Linux swap / Solaris

Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4982    40017883+  83  Linux

---

### Post by logos34 on 2007-06-23
> I formatted it in etc3 using Gparted

...

The previous drive was formatted in NTFS.

So that means the filesystem type has changed and fstab still has the old entry with 'ntfs', when it should be 'ext3'.  AND the UUID's may be another factor.

---

### Post by guddr on 2007-06-23
I appreciate the info. How do I go about fixing my problem/

---

### Post by guddr on 2007-06-23
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=5813bc4f-c17b-4955-911a-e3b2c894c62f / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=259f0aa6-59ce-40fc-99ad-babebbb127d6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hdb1 /media/HD30\040 ntfs-3g defaults,locale=en_US.UTF-8 0 0
macd@macd-desktop:~$

---

### Post by logos34 on 2007-06-23
try:

**gksudo gedit /etc/fstab**

change thus:

> /dev/hdb1 /media/HD30\040 **ext3 defaults,errors=remount-ro 0 1**

save and close.
[B]
sudo mount -t auto /dev/hdb1 /media/HD30\040[/B]

The 'auto' will use the filesystem as listed in fstab.

---

### Post by guddr on 2007-06-23
Hello,  Here is what I get back from the second step of your suggestion.What am I doing wrong?

macd@macd-desktop:~$ sudo mount -t auto /dev/hdb1 /media/HD30\040
mount: mount point /media/HD30040 does not exist
macd@macd-desktop:~$

---

### Post by logos34 on 2007-06-23
sorry for the tardy reply...

You say you're using the same mount point as the old one...maybe that '\' backslash is not working.  Not sure...Look in /media -- is there a mount point with the name you specified?

You could just create another one and try mounting it there...

[B]sudo mkdir /media/whatever
[/B]
Change fstab to match and try mounting again.

---

### Post by guddr on 2007-06-23
I am trying to mount a replacement slave drive formatted in etc3 for one formatted using ntsf.  I cant seem to find the correct command for this.  Can anyone help me?  Thanks.


dev/hdb1 /media/HD30\040 ext3 defaults,errors=remount-ro 0 1

macd@macd-desktop:~$ sudo mount -t auto /dev/hdb1/media/HD30\040
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
For many more details, say  man 8 mount

---

### Post by guddr on 2007-06-23
I am trying to mount a replacement slave drive formatted in etc3 for one formatted using ntsf. I cant seem to find the correct command for this. Can anyone help me? Thanks.


dev/hdb1 /media/HD30\040 ext3 defaults,errors=remount-ro 0 1

macd@macd-desktop:~$ sudo mount -t auto /dev/hdb1/media/HD30\040
Usage: mount -V : print version
mount -h : print this help
mount : list mounted filesystems
mount -l : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
mount -a [-t|-O] ... : mount all stuff from /etc/fstab
mount device : mount device at the known place
mount directory : mount known device here
mount -t type dev dir : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
mount --bind olddir newdir
or move a subtree:
mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using -L label or by uuid, using -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say man 8 mount
__________________

---

### Post by logos34 on 2007-06-23
> sudo mount -t auto /dev/hdb1/media/HD30\040

first of all you didn't copy it correctly-- there should be a space hdb1 and /media...

like this

sudo mount -t auto /dev/hdb1 /media/HD30\040

or 

sudo mount -t ext3 /dev/hdb1 /media/HD30\040

but try creating another mount point and mounting it there.  Like:
[B]
sudo mkdir /media/hdb1 
sudo mount -t auto /dev/hdb1 /media/hdb1[/B]
or 
**sudo mount -t ext3 /dev/hdb1 /media/hdb1**

---

### Post by guddr on 2007-06-23
Hey, I got it mounted in the new directory, HD40.  It now shows up in Home.  However, it does have a lock on it. Do I remove it or just add data to this drive?

---

### Post by logos34 on 2007-06-23
right click on it>properties>permissions

---

### Post by logos34 on 2007-06-23
so you created a new dir '/media/HD40' and mounted it there?  Remember to change fstab

---

### Post by guddr on 2007-06-23
It says im not the owner so I cant change anything.

---

### Post by logos34 on 2007-06-23
edit fstab so that the mount point matches.  Then reboot and see if it automount correctly with permissions.

---

### Post by guddr on 2007-06-23
I did make a new directory and I changed fstab.  It is good to see the HD under Home.  I never thought I'd get this far.  I really appreciate your help.  I just need to unlock the HD and im home free.  Thanks again.

---

### Post by guddr on 2007-06-23
It is still locked after rebooting.  Here is my fstab info:

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=5813bc4f-c17b-4955-911a-e3b2c894c62f / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=259f0aa6-59ce-40fc-99ad-babebbb127d6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hdb1 /media/HD40 ext3 defaults,errors=remount-ro 0 1
macd@macd-desktop:~$

---

### Post by logos34 on 2007-06-23
**sudo chmod 755 -R /media/HD40**

The "-R" switch tells chmod to work on all files and sub-directories in /media/HD40. This command will give only the owner of te files read/write/execute permission so you probably want to make yourself the owner also (as opposed to the owner being root)

**sudo chown userid:userid  -R /media/HD40**

you could also use chmod 777 (everyone has access

hope that works.  permissions is not really my strong point

---

### Post by logos34 on 2007-06-23
or open nautilus as root, right-click on /media/HD40 and try to change permissions that way

**gksudo nautilus**

---

