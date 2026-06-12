---
title: "Hard Drive Permisson"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by tyler71 on 2006-07-20
I just installed Ubuntu on a seperate, and for some reason I don't have permission to access my main hard drive (Windows) which has all my mp3's on it. I've tried to change permissions but it is turning out to be impossible.
Here's a shot of what's happening.
Thanks tyler71.
[IMG]http://tyler71.t35.com/pics/Screenshot-1.jpg[/IMG]

---

### Post by swamytk on 2006-07-20
1. Open /etc/fstab file:
$sudo gedit /etc/fstab

2. Add this option *umask=0000* in your windows partition entry, which may be /dev/sda1. By default option will be something like *default*, put a comma and add this.

---

### Post by OU812 on 2006-07-20
If your partition is ntfs I would use

ro,users,umask=0222

IMHO you either keep defaults or you delete it and add your modifications. I chose umask=0222 because I use

rw,users,umask=000

for my vfat partitions.

john

@syamytk: what is the difference between umask=0222, 000, and 0000? Thanks.

---

### Post by tyler71 on 2006-07-20
I current dont have the hard drive there,

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Is what is shown, what do I do?

---

### Post by OU812 on 2006-07-21
Ok. Copy and paste this anywhere in fstab. Note: If you put this at the end of fstab, you must hit enter at the end of the line (fstab must have a newline and the end of file).

```
/dev/hda1       /mnt/win_c      ntfs ro,users,umask=0222 0 0
```

Note: change "win_c" to any name that makes sense to you. Then open a terminal and enter

```
sudo mkdir /mnt/win_c
```

Then reboot. Your partition should then be visible. Open places>home_folder and navigate to /mnt/win_c. Note: If you have multiple win partitions, let me know so I can show you how to set them up.

john

---

