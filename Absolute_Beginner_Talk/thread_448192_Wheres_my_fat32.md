---
title: "Wheres my fat32?"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Ramthebuffs on 2007-05-18
Just got the dual setup, now how do I find my fat32?

---

### Post by BarfBag on 2007-05-18
You have to mount it.

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by taurus on 2007-05-18
From

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
Then, mount that fat32 partition before you can use/access it.

---

### Post by starcraft.man on 2007-05-18
It should have been automatically mounted by the installer in most cases. Just to be sure you still have it... run this in terminal:

```
sudo fdisk -ls
```
Check that there is a fat32 partition.

Assuming it is still on your drive and not accidentally overwritten, use this guide to mount the partition. [Link.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite") 

That should be it, have a nice day :).

Edit: taurus, there ya are :p I was wondering when you'd next "coincidentally" beat my post by a millisecond. :p

---

### Post by Ramthebuffs on 2007-05-18
thanks guys, managed to find it.  For some reason it seems like I have the same Fat32 twice with one haveing (LBA) behind it.  Not sure why, but that didn't work, so the obvious choice was the other one.

---

### Post by starcraft.man on 2007-05-18
Hmmm, kinda odd... you sure its the exact same partition? If its just a messed up version of the one you were looking for, guess ya should delete it. Might want to look into it further though.

Glad to be of help though, have a great time with Ubuntu :).

---

### Post by taurus on 2007-05-18
I bet the first one is an extended partition while the second entry is the actual fat32 partition.

p.s.  And hello starcraft.man...

---

### Post by starcraft.man on 2007-05-18
> **taurus said:**
> I bet the first one is an extended partition while the second entry is the actual fat32 partition.

Righto, my bad... Imma wee bit sleepy guess (was long day), shoulda thought of that :). taurus always nearby with the answer :D

Edit: Rofl, hello there taurus :D Imagine running into you again, small world :p.

---

### Post by Ramthebuffs on 2007-05-19
I'm having some issues getting this to automount on boot.  Heres my fstab, I added the hda5 line, but its not working.  Any ideas?

>  GNU nano 1.3.12             File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=815d3b12-1e1b-4eb6-b8d8-ac599ebba164 /               ext3    defaults,erro$

/dev/hda5 /media/windows -t vfat -o iocharset=utf8,umask=000 0 0

# /dev/hda6
UUID=1ae62d35-f513-49f0-a862-aa3a08f967f4 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


---

