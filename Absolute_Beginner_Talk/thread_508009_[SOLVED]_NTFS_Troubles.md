---
title: "[SOLVED] NTFS Troubles"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by WarholsGhost on 2007-07-23
so i downloaded the NTFS driver and it won't let me make the internal drive writeable. Please help

It just has the option of making external devices writeable. the external one is not selectable

---

### Post by WarholsGhost on 2007-07-23
Well i got the hard drive working but i have some problems

1. i can't un mount the hard driver
2. i can't rename the hard drive.

please help!

---

### Post by benx009 on 2007-07-23
make sure that no other program is accessing your ntfs drive (media player, text editor, image editor, etc.)  then unmount and remount your ntfs drive.  see if ntfs-3g will work then.  if not, restart your system and try again (**anything** accessing the ntfs drive will not allow the driver to work; even something like your desktop background could be a candidate, if it is really on your ntfs drive)

EDIT: oh, goody, you got it to work:)

to unmount, once again, make sure no program is accessing your drive.

---

### Post by WarholsGhost on 2007-07-23
this is the error i'm getting

[http://img.photobucket.com/albums/v448/Warholsghost/Screenshot.png](http://img.photobucket.com/albums/v448/Warholsghost/Screenshot.png)

---

### Post by WarholsGhost on 2007-07-23
i still need help

---

### Post by kelvin spratt on 2007-07-23
IF your using any of the 7..04 versions the drivers are already in the repro go in synaptic Ntfs3g and install
then go into menu and enable ntfs  Shut-down your computer and restart into windows 2 times in right hand bottom tool bar safely remove any usb and clear, you don't need to unplug anything. restart into linux your drives should now mount and any USB drive will also

---

### Post by ravenwere on 2007-07-23
When you try to umount the hdd are you using the root command or a root shell??

```

sudo mount /dev/yourpartition

```

r

---

### Post by WarholsGhost on 2007-07-24
i'm right clicking and selecting unmount

---

### Post by KyleBrandt on 2007-07-24
WarholsGhost:  I would recommend mounting and unmounting from the command line (terminal).  I have always found mounting in nautilus (the graphical file browser) to be flaky myself.  Also if you install pmount "sudo apt-get install pmount"  It can make mounting and unmount a little bit easier.  You would use the commands pmount and punmount.  So say you ntfs parition is /dev/hda1, you should be able to get away with pmount /dev/hda1.

You can rename your ntfs parition with the ntfslabel command.  Type ntfslabel -h for its usage.

---

### Post by ravenwere on 2007-07-24
The screenshot error message you post indicates that the unmount (or mount) command requires you to be logged on as root.

The best way is to initiate a terminal and use the commands below. I agree with Miles800 particularly with NTFS on linux, it does not behave itself when using the gui menu.

You can mount and unmount by using the terminal:
```
sudo mount /dev/yourpartition
``` or
```
sudo umount /dev/yourpartition
```

Replace yourpartition, of course, with your partion name

Yet another way would be to press ALT + F2 and type in on KDE "kdesu mount /dev/yourpartition"
or if using gnome "gksudo mount /dev/yourpartition"

Works definitely for Kubuntu. Should do for Gnome.

All the best,
r

---

### Post by WarholsGhost on 2007-07-24
thanks both of you, it worked for unmounting and mounting

but i still have a problem with renaming (i may be running in to the problem because i accidentally named my drive "Desktop")

but here is what terminal is giving me. 



gregg@gregg-desktop:~$ ntfslabel -f Desktop storage
Desktop is not a block device, nor regular file.
Forced to continue.
Error opening partition device : Is a directory
Failed to startup volume : Is a directory
Couldn't mount device 'Desktop' : Is a directory

---

### Post by Rocket2DMn on 2007-07-24
I've never used ntfslabel, but you probably have to give the full directory path to the device, like
```
ntfslabel /media/Desktop storage
```
or perhaps you need the
```
ntfslabel /dev/* storage
//where * is the device listed in:
sudo fdisk -l
//for your ntfs partition
```
Be careful with the force option (-f).

---

### Post by WarholsGhost on 2007-07-24
ok so i did
gregg@gregg-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9375    75304656   83  Linux
/dev/hda2            9376        9729     2843505    5  Extended
/dev/hda5            9376        9729     2843473+  82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36480   293025568+   7  HPFS/NTFS

Then..

gregg@gregg-desktop:~$ ntfslabel /dev/hdb1 storage
The device /dev/hdb1, is mounted.
Use the force option to work a mounted filesystem.
gregg@gregg-desktop:~$ ntfslabel -f /dev/hdb1 storage
The device /dev/hdb1, is mounted.
Forced to continue.
Error opening partition device : Permission denied
Failed to startup volume : Permission denied
Couldn't mount device '/dev/hdb1' : Permission denied

---

### Post by Rocket2DMn on 2007-07-24
You need to unmount the drive first (it must remain plugged into the computer)
```
sudo umount /media/Desktop
sudo ntfslabel /dev/hdb1 storage
sudo mount -a
```
This assumes you have the drive mounted at /media/Desktop.  Replace with your mount point.
mount -a works only if you have the drive declared in /etc/fstab
Please show the output of
```
cat /etc/fstab
```

---

### Post by WarholsGhost on 2007-07-24
Code:
> 
gregg@gregg-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=9d53c1f5-9dc6-4ec1-84eb-65bf0bf14796 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=94aac2b6-06e3-4376-9da8-1b59c2f26191 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hdb1 /media/Desktop ntfs-3g defaults,locale=en_US.UTF-8 0 0


---

### Post by Rocket2DMn on 2007-07-24
Heh, this should be a simple fix:  Change the line 
"/dev/hdb1 /media/Desktop ntfs-3g defaults,locale=en_US.UTF-8 0 0"
to
"/dev/hdb1 /media/storage ntfs-3g defaults,locale=en_US.UTF-8 0 0"
by running 
```
sudo umount /media/Desktop
gksudo gedit /etc/fstab
sudo mount -a
```

---

### Post by WarholsGhost on 2007-07-24
gregg@gregg-desktop:~$ sudo mount -a
fusermount: failed to access mountpoint /media/storage: No such file or directory
FUSE mount point creation failed
Unmounting /dev/hdb1 (storage)


now what?

---

### Post by Rocket2DMn on 2007-07-24
oops, you have to make the directory first (this is the only time you have to do it)
```
sudo mkdir /media/storage
```
Then mount.

---

### Post by WarholsGhost on 2007-07-24
YESSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


thank you for the help, now it works!

---

### Post by gn2 on 2007-07-24
One sure fire way to avoid going round in circles wasting time is to use the NTFS/Fat32 Auto Mounting utility that's available through Automatix, listed in the Miscellaneous category once you've got Automatix installed.
Automatically mounts NTFS dries/partitions and makes them writeable.
.
Automatix has it's own support forums should you require them.
.
[www.getautomatix.com](www.getautomatix.com)
.

---

