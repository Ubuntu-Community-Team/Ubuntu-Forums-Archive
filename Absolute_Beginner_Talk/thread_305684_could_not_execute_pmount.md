---
title: "could not execute pmount"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by Bad Apple on 2006-11-23
ubuntu wont seem to allow me access to a 12.5gb partition of my drive, 

it just says

error: devive /dev/hda1 is not removable
error: could not excecute pmount

---

### Post by taurus on 2006-11-23
How did you try to mount it?  Is it fat32 or NTFS filesystem?

---

### Post by Bad Apple on 2006-11-23
its extended 3, and i am just double clicking it from the places browser

tried to format, doesnt appear to do anything. says (free space unavailable)

---

### Post by taurus on 2006-11-23
What are the outputs of these commands from a terminal, Applications -> Accessories -> Terminal?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Bad Apple on 2006-11-23
no such file or directory

---

### Post by taurus on 2006-11-23
You mean no "cat /etc/fstab"???

Instead of typing (probably typo), try to do the cut 'n paste.  Cut with the left button and paste the result with either the middle button if you have one or hold down both left and right buttons at the same time!

---

### Post by Bad Apple on 2006-11-24
first command out puts
```
Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1636    13141138+  83  Linux
/dev/hda2            3416        3648     1871572+   5  Extended
/dev/hda3   *        1637        3415    14289817+  83  Linux
/dev/hda5            3496        3648     1228941   82  Linux swap / Solaris/dev/hda6            3416        3495      642537   82  Linux swap / Solaris
Partition table entries are not in disk order

```

second command outputs

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by anaconda on 2006-11-24
> **Bad Apple said:**
> 
error: devive /dev/hda1 is not removable
error: could not excecute pmount

That tells it all.
You are trying to use pmount, which works ONLY for removable devices. And hda1 is a fixed hard drive, so it wont mount like that.

Here is how you can mount it manually using terminal:
```
sudo mkdir /mnt/disk
sudo mount -t auto /dev/hda1 /mnt/disk
```

after those commands you can access your hda1 partition from folder /mnt/disk 

if you dont have enough rights to read/write to that partition you can always use "sudo nautilus" to get file browser with admin rights..

If you dont want to mount it manually every time you boot your machine you might want to add your hda1 to your /etc/fstab file. then it will be mounted automatically each time you boot your machine....

This link might be of interest:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

