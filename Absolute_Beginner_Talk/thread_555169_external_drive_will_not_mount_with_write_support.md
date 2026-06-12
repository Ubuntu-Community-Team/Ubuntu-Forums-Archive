---
title: "external drive will not mount with write support"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by rude_lee on 2007-09-19
external drive will not mount with write support 
it is nfts it was set up when i had windows on my lap top but i only got ubuntu now and for some reason it wont mount no more 
i got lots of stuff on it i dont want to lose 
some help please

---

### Post by rude_lee on 2007-09-19
this is wat i get for 
sudo fdisk -l
df -h
cat /etc/fstab




Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11808    94847728+  83  Linux
/dev/hda2           11809       12161     2835472+   5  Extended
/dev/hda5           11809       12161     2835441   82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

---

### Post by Bushfire on 2007-09-19
Firstly, what version of Ubuntu are you using? Anything before 7.04 ship with read only driver support for NTFS.

And second, what command/tool are you  using to mount it? It should be something along these lines (if using CLI):
```
$ sudo mount -t ntfs /dev/sda1 *(directory where you want it mounted)*
```

---

### Post by rude_lee on 2007-09-19
ubuntu 7.04 i365 with ntfs configuration tool it can read but i need it to write
wat is CLI

---

### Post by Maxtorm on 2007-09-19
> **rude_lee said:**
> external drive will not mount with write support 
it is nfts ...
Try this: go to Applications, Accessories, Terminal. At the prompt, type
```
sudo apt-get install ntfs-3g
```and hit Enter. It will ask you for your password. Type it in and press Enter. 

This will install the ntfs drivers for write access to your drives.

Also, you'll need ntfs-config (see: [http://ubuntuforums.org/showthread.php?t=555142](http://ubuntuforums.org/showthread.php?t=555142)).  Install it with the same command, replacing ntfs-3g with ntfs-config (in hindsight, installing ntfs-config likely installs ntfs-3g as a dependent package).

---

### Post by rude_lee on 2007-09-19
it says it got all that in already but it will not mount write but will mount write read

---

### Post by Maxtorm on 2007-09-19
> **rude_lee said:**
> it says it got all that in already but it will not mount write but will mount write read
Isn't that what you want (i.e. read/write access)? I don't think it is possible to mount as write-only.

---

### Post by rude_lee on 2007-09-19
sorry yeah i want both but im gettin only read sorry

---

### Post by Maxtorm on 2007-09-19
I'm learning on the go here too.  This page describes ntfs-config in detail: [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by rude_lee on 2007-09-20
i see but i dont have windows on my harddrive just fiesty and it and the hardrive i want read/write support for is external

---

### Post by Maxtorm on 2007-09-20
That's OK -- it will still work.

---

### Post by rude_lee on 2007-09-25
nope it did not work at all so i opened the properties of the drive and configured it that way now it will not mount at all

---

### Post by rude_lee on 2007-09-25
this is wat i get

root@rude-laptop:~#  mount -t ntfs-3g/dev/sda1/media/SEA_DISC -o force
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

---

### Post by rude_lee on 2007-09-25
any help

---

### Post by rude_lee on 2007-09-25
sudo fdisk -l
cat /etc/fstab
dmesg | grep dvd

this is wat i get
rude@rude-laptop:~$ sudo fdisk -l

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11808    94847728+  83  Linux
/dev/hda2           11809       12161     2835472+   5  Extended
/dev/hda5           11809       12161     2835441   82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS
rude@rude-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=cd1fff2f-2596-4b40-a669-1688292f442a / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=079ed03a-84d6-487d-a9df-e3ed7740634a none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
rude@rude-laptop:~$ dmesg | grep dvd

and my fstab gives me

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=cd1fff2f-2596-4b40-a669-1688292f442a / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=079ed03a-84d6-487d-a9df-e3ed7740634a none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

will this help fix it

---

