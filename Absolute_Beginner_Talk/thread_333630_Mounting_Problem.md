---
title: "Mounting Problem"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by brisingr_dagger on 2007-01-07
:cry:  im new to ubuntu and am there for having some difficulty with mounting my windows fat32 partition so i can view it in ubuntu i had it working for a short time but then my computer switched off and when i swithed it back on again there was nothing in my windows folder??? :???:

---

### Post by Waappu on 2007-01-07
Hi

This might help you
[https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html)

---

### Post by taurus on 2007-01-07
Paste the output of this command from a terminal here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by brisingr_dagger on 2007-01-07
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3463    27816516    c  W95 FAT32 (LBA)
/dev/hda2            3464        4865    11261565    5  Extended
/dev/hda5            3464        4737    10233373+  83  Linux
/dev/hda6            4738        4865     1028128+  82  Linux swap / Solaris
backupadmin@ubuntu:~$

---

### Post by Waappu on 2007-01-07
Hi

Make directory where you want to mount new drive e.g.
```
mkdir /mnt/fat
```
then backup and edit /etc/fstab file
```
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
```
add this to file
> /dev/hda1 /mnt/fat vfat umask=0000 0 0
Then mount new drive
```
sudo mount -a
```
and you can access drive from /mnt/fat

---

### Post by brisingr_dagger on 2007-01-07
i've gone through all tht and it's still now working ](*,)

---

### Post by taurus on 2007-01-07
It's not working or it is working!

If I were you, I would do something like this.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Scroll to the end of the file and add the following line to it.

```
/dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=000   0   0
```
Save the change.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hda1
sudo mount -a
df -h
```
Or reboot your machine if you wish.

---

### Post by brisingr_dagger on 2007-01-07
now im getting this message 
[mntent]: line 15 in /etc/fstab is bad

---

### Post by taurus on 2007-01-07
Post your /etc/fstab!

```
cat /etc/fstab
```

---

### Post by brisingr_dagger on 2007-01-07
# /etc/fstab: static file system information.


#


# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1

/dev/hda6       none            swap    sw              0       0

/dev/hda1       /media /windows        ntfs    nls=utf8,umask=0222        0       0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

/dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=000   0   0

---

### Post by taurus on 2007-01-07
How did you get this line in /etc/fstab anyway?

```
/dev/hda1 /media /windows ntfs nls=utf8,umask=0222 0 0
```
Remove it and save it.  Then, continue with my directions.

---

### Post by Waappu on 2007-01-07
Hi

Edit /etc/fstab file
```
sudo gedit /etc/fstab
```
Remove this line because you don't  have NTFS parition
> /dev/hda1       /media /windows        ntfs    nls=utf8,umask=0222        0       0
and change this
> /dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=000   0   0
to this one
> /dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=0000   0   0

---

### Post by taurus on 2007-01-07
> **Waappu said:**
> Hi

Edit /etc/fstab file
```
sudo gedit /etc/fstab
```
Remove this line because you don't  have NTFS parition

and change this

to this one

You should use "gksudo" instead of "sudo" when you run gedit.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Also, umask can be used with 000 instead of 0000.  They both mean the same!

---

### Post by Waappu on 2007-01-07
> **taurus said:**
> You should use "gksudo" instead of "sudo" when you run gedit.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Also, umask can be used with 000 instead of 0000.  They both mean the same!

Thanks =). I didn't know that

---

### Post by brisingr_dagger on 2007-01-07
thanks alot guys/girls it's sorted now :D

---

