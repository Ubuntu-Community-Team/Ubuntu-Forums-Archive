---
title: "Disk managing(ish)"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by SandersCraddock on 2006-12-09
Ok so I have 2 hard drives and decided that I would stick ubuntu on one of them and windows on the other. Ubuntu hd is about 12gig whereas windows is 120gig. I was assuming that I would be able to use both disks from the ubuntu operating system, however this does not seem to be the case. I checked the help files and it tokd me something about a program (in ubuntu) that i could use to make the windows hd visible, to my surprise i found this program did not exist. I checked around on ubuntu and there are sevral programs for disks and whatnot but none of them let me do what I want to do. Anyone got any ideas:-D ?

---

### Post by aidanr on 2006-12-09
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)

---

### Post by kane77 on 2006-12-09
what filesystem is on the windows partition? (ntfs or fat32?)
anyways for ntfs disks you should be able to read from it but not write...
If you dont already have that drive visible try adding a line in your fstab (run ```
sudo gedit /etc/fstab
```
and add these line```

/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
```
(replace /dev/sda1 with the name of your device (sda1 for primary sata disks or hda1 for primary ata disk..))

for fat32 you can have both read and write permissions.
run ```
sudo gedit /etc/fstab
```
```
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       0
```
(again replace /dev/hda1  with appropriate name...
for viewing your linux partition under windows you can use any of free utilities such as ext2read ([http://www.brothersoft.com/utilities/miscellaneous/ext2read_11893.html](http://www.brothersoft.com/utilities/miscellaneous/ext2read_11893.html)) or for example total commander powerpack has a ext2 browser...

---

### Post by SandersCraddock on 2006-12-12
Cheers guys will try these ideas out when I have my wireless adapter sorted.

Alex Craddock

---

