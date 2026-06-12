---
title: "Read only auth. for some windows folder"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by nir78 on 2006-04-06
Hi,

I mounted my old windows folder and I can read\write to them freely (all FAT32).
For a reason, some folders are in read only mode... how can I change it ??

Nir

---

### Post by aysiu on 2006-04-06
[QUOTE=nir78]Hi,

I mounted my old windows folder and I can read\write to them freely (all FAT32).
For a reason, some folders are in read only mode... how can I change it ??

Nir[/QUOTE] You wouldn't happen to have two entries for the same partition in your /etc/fstab, would you? Can you post the output of this terminal command? ```
cat /etc/fstab
```

Gnome: Applications > Accessories > Terminal
KDE: KMenu > System > Konsole

---

### Post by nir78 on 2006-04-06
Hi,

Don't think I have one.. but here it is:
```
nir@main-storage:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda5     /media/multimedia  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb1     /media/new_win  vfat    iocharset=utf8,umask=000   0       0
/dev/sda1     /media/old_win  vfat    iocharset=utf8,umask=000   0       0
nir@main-storage:~$


```

Nir

---

### Post by aysiu on 2006-04-06
No duplicates I can see.

You may want to try remounting at a different mount point, though, instead of within the /media or /mnt folders. Try a new static folder (you'll have to create the folder first:  ```
sudo mkdir /folder_name
```) as the mount point instead.

---

### Post by nir78 on 2006-04-06
Is there a way I can change the problematic folder auth. insted of changing the mount point ?

---

### Post by aysiu on 2006-04-06
[QUOTE=nir78]Is there a way I can change the problematic folder auth. insted of changing the mount point ?[/QUOTE] I don't know.

---

