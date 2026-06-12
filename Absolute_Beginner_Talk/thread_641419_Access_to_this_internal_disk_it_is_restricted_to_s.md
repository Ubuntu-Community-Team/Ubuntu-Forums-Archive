---
title: "Access to this internal disk it is restricted to system administrators....."
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by dcipher on 2007-12-15
Please help me......m using Ubuntu 7.10, I'm getting a bit frustrated at receiving the following message:


Access to this internal disk it is restricted to system administrators.....

i have formatted one of ma partition using gnome partition editor from a live disk.....
after dat.....dat partition of ma harddisk not auto mount on logon.

when i try to open it from "computer"....it ask for password den it mount it

after giving password it works properly as usual.....but i dont want to give pass word everytime i logon...

i m sure i missing sumthing.....can u plz help me out of this...

---

### Post by taurus on 2007-12-15
Is it ntfs filesystem?  It's best to use ntfs-3g driver to mount it and you want to have it mount automatically each time you boot.  You can do that by adding an entry in /etc/fstab.

Post the output of these two commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
cat /etc/fstab
```

---

### Post by dcipher on 2007-12-16
> **taurus said:**
> Is it ntfs filesystem?  It's best to use ntfs-3g driver to mount it and you want to have it mount automatically each time you boot.  You can do that by adding an entry in /etc/fstab.


yes it is ntfs file system......before formatting...ubuntu ws mount it automattically....but after formatting it always ask for password to mount it when i logon...

output:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe793e793

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       30401   213479752+   5  Extended
/dev/sda5            3825       16572   102398278+   7  HPFS/NTFS  [COLOR="Red"]<- this is problem drive[/COLOR]
/dev/sda6           16573       21794    41945683+   b  W95 FAT32
/dev/sda7           21795       25710    31455238+   b  W95 FAT32
/dev/sda8           25711       25959     2000061   82  Linux swap / Solaris
/dev/sda9           25960       30401    35680333+  83  Linux

OUTPUT II:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=9c88a9ee-52d1-4c6d-a6b8-758f1b215f6a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=A4C85917C858E956 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=04B0CE35B0CE2D4C /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=4751-747A  /media/sda6     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=4751-74CD  /media/sda7     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda8
UUID=bb3aebe6-14d5-4142-aa6d-c8d409d08c4e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


plz help me....

---

### Post by taurus on 2007-12-16
When you format a partition, you change the UUID so the one from /etc/fstab won't match with your /dev/sda5 anymore.  So, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace the current entry for /dev/sda5 

```

# /dev/sda5
UUID=04B0CE35B0CE2D4C /media/sda5 ntfs defaults,umask=007,gid=46 0 1

```
with with this one.

```
/dev/sda5   /media/sda5   ntfs-3g   defaults   0   0
```
Save it.  Then, make sure you have ntfs-3g installed before you reboot your machine.

```
sudo apt-get update
sudo apt-get install ntfs-3g
```
Now, reboot and see if /dev/sda5 is mounted to /media/sda5.

```
df -h
```

---

### Post by dcipher on 2007-12-16
thanks.....it worked....now ubuntu mounts it automaticaly on logon....

---

