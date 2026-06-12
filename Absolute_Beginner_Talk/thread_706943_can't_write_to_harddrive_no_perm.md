---
title: "can't write to harddrive no perm"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Doorslammer on 2008-02-24
```
doorslammer@ubuntuslammer:~$ ls -la /media
total 84
drwxr-xr-x  7 root        root   4096 2008-02-24 15:51 .
drwxr-xr-x 21 root        root   4096 2008-02-01 19:03 ..
lrwxrwxrwx  1 root        root      6 2008-01-31 15:33 cdrom -> cdrom0
drwxr-xr-x  2 root        root   4096 2008-01-31 15:33 cdrom0
drwxr-xr-x  2 root        root   4096 2008-02-08 09:55 data
lrwxrwxrwx  1 root        root     45 2008-01-31 16:00 .directory -> /etc/kubunt          u-default-settings/directory-media
lrwxrwxrwx  1 root        root      7 2008-01-31 15:33 floppy -> floppy0
drwxr-xr-x  2 root        root   4096 2008-01-31 15:33 floppy0
-rw-r--r--  1 root        root      0 2008-02-24 15:45 .hal-mtab
-rw-------  1 root        root      0 2008-02-24 15:51 .hal-mtab-lock
lrwxrwxrwx  1 root        root     42 2008-01-31 16:00 .hidden -> /etc/kubuntu-d          efault-settings/hidden-media
drwxrwx---  5 doorslammer users 32768 1969-12-31 19:00 sda1
drwxrwx---  6 doorslammer users 32768 1969-12-31 19:00 sdb1
doorslammer@ubuntuslammer:~$
 
```
not sure how to go about changing it 
had it all working  but today had power outage 
next thing I know I can't write to that drive  sdb1 (seems to be owned by root) it's a fat32 file system

---

### Post by Doorslammer on 2008-02-24
I can see the drive  I just can't write to it

never mind : reboot fixed the problem

---

