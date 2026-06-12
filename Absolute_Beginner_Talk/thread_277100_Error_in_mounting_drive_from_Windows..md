---
title: "Error in mounting drive from Windows."
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Eugene Khoo on 2006-10-14
HI, I am new to Linux, I installed it on a totally separate HDD and have some other HDDs where I store my documents and other media.  I can view it when I try to find files/folders and do a browse of the storage media.  However, when I try to actually view the contents, the message "mount: can't find /dev/hdb1 in /etc/fstab or /etc/mtab" appears.  Appreciate if someone could offer some advice.  Thanks

Eugene

---

### Post by meng on 2006-10-14
The double-click mount (using pmount) won't work by default. You should check out the wiki:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by jorn on 2006-10-14
Welcome#!
Your partition hdb1 might not be mounted correctly.
All partitions are listed i /etc/fstab and are mounted at boottime.
If hdb has got a fat or ntfs-filesystem (mswindows) you might look here.
[http://easylinux.info/wiki/Ubuntu_dapper#Windows](http://easylinux.info/wiki/Ubuntu_dapper#Windows)
If you want more specific help, please paste into terminal:
> sudo fdisk -l 
and post it.
Paste into terminal:
> sudo gedit /etc/fstab
and post it.

---

