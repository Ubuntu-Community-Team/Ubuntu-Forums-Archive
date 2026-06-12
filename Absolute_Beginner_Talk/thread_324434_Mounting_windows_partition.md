---
title: "Mounting windows partition"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by herrma29 on 2006-12-23
Ok, so I am trying to mount my partition and I want to make sure I am doing everythign right.

chris@chris-laptop:~$ sudo fdisk -l

Disk /dev/sda: 99.8 GB, 99830223360 bytes
255 heads, 63 sectors/track, 12137 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5332    42829258+   7  HPFS/NTFS
/dev/sda2            5333       11952    53175150   83  Linux
/dev/sda3           11953       12137     1486012+   5  Extended
/dev/sda5           11953       12137     1485981   82  Linux swap / Solaris

Next, I made the directory 'windows'

and backed up my fstab file

but when I get to this part:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=345d621c-ccf6-4811-ac84-a1100192940c /               ext3    defaults,erro$
# /dev/sda5
UUID=a44d1a99-eb67-48e7-b36f-17f28afa08d6 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

I don't know exactly what to change. My windows partition isn't listed in this like I was thinking it was supposed to be, and I don't want to screw my computer up too much :rolleyes: 

Could anyone help me figure out what I need to add to this file to make my windows partition available? Thanks a lot!

---

### Post by herrma29 on 2006-12-23
ok, so I added this:

#/dev/sda1 /windows ntfs nls=utf8,umask=0222 0 0

to my file and finished up the instructions on the page. I went to the windows folder on my file browser and there is nothing in it. Any pointers?

---

### Post by taurus on 2006-12-23
You need to remove the # so it would look like this in your /etc/fstab...

```
/dev/sda1  /windows  ntfs  nls=utf8,umask=0222  0  0
```

---

### Post by angkor on 2006-12-23
> **taurus said:**
> You need to remove the # so it would look like this in your /etc/fstab...

```
/dev/sda1  /windows  ntfs  nls=utf8,umask=0222  0  0
```

After that you can then reboot to have the partition mounted or enter:

```
sudo mount -a
```

to remount all drives without rebooting.

---

### Post by herrma29 on 2006-12-24
Just wanted to say thanks for the help :)

---

