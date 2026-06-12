---
title: "share files between mac and ubuntu partitions"
date: 2008-08-22
forum: Apple Hardware Users
---

### Post by bigdee973 on 2008-08-22
sorry i posted this in another group... i didnt knwo there was an apple section i didnt see it..

hello im having a very stupid problem..my mac operating system is having problems and i need to backup some very very important documents. i use ubuntu live cd and mac hard drive is mounted. i can see the files that i want to backup on my mac partition and i can even open the files and save them but when i just try to copy and paste the file onto my external hard drive i get permission denied... i used sudo nautilus ... from sudo nautilus i can actually open the file (pdf files) and then save them onto my external hard drive but the issue is that i have ALLLLOTT OF PDF and doc files. now this is stupid..i can open the file and save but i cannot copy and paste them... whats going on here? okay so i need to know if i installed ubuntu onto the mac will i be able to have full read and/or write permissions or will i still get permission denied messages even after i install ubuntu? if i do then what must i do in order to at least copy the files to back them up..im so close and i really really need these files...they are for court.

---

### Post by _mario_ on 2008-08-23
Usually filesystems store numerically IDs assigned to each user/group to describe access permissions. Unfortunately Ubuntu and MacOS use different IDs.

I don't believe that installing onto harddisk makes a difference. I installed Ubuntu alongside MacOS. After mounting the MacOS partition to /media/macosx its content looks like this:

```

drwxrwxr-x 1 root   80   34 2008-08-01 19:52 Applications/
drwxr-xr-x 1 root root   40 2008-06-09 13:13 bin/
drwxrwxr-t 1 root   80    2 2008-01-29 03:22 cores/
dr-xr-xr-x 1 root root    2 2008-01-29 03:22 dev/
drwxrwxr-x 1 root   80    3 2008-04-30 16:28 Developer/
drwxrwxr-x 1 root   80    7 2008-04-13 01:54 efi/
lrwxr-xr-x 1 root   80   11 2008-04-11 17:01 etc -> private/etc/
dr-xr-xr-x 1 root   80    2 2008-04-11 17:12 home/
drwxrwxr-t 1 root   80   49 2008-04-11 17:07 Library/
-rw-r--r-- 1 root root 9,9M 2008-06-10 04:37 mach_kernel
-rw-r--r-- 1 root root  11M 2008-06-10 04:37 mach_kernel.ctfsys
dr-xr-xr-x 1 root   80    2 2008-04-11 17:12 net/
drwxr-xr-x 1 root root    2 2008-01-29 03:22 Network/
drwxr-xr-x 1 root root    6 2008-04-11 17:05 private/
drwxr-xr-x 1 root root   66 2008-06-09 13:13 sbin/
drwxr-xr-x 1 root root    4 2008-06-09 13:15 System/
lrwxr-xr-x 1 root   80   11 2008-04-11 17:01 tmp -> private/tmp/
drwxr-xr-x 1 root   80    5 2008-04-11 17:16 Users/
drwxr-xr-x 1 root root   11 2008-04-11 17:21 usr/
lrwxr-xr-x 1 root   80   11 2008-04-11 17:01 var -> private/var/
drwxrwxrwt 1 root   80    3 2008-08-19 17:10 Volumes/

```

As you can see some files/directories belong to group 80, which would have been the group admin in MacOS (according to /media/macosx/etc/group), but isn't defined in Ubuntu. Looking into /media/macosx/Users yields this:

```

drwxr-xr-x 1  501 dialout 18 2008-08-19 15:11 mario/
drwxrwxrwt 1 root root     4 2008-04-26 20:18 Shared/

```

My MacOS's home directory (mario) belongs to user ID 501 (undefined in Ubuntu) and group dialout (Ubuntu dialout -> numerically 20 -> MacOS staff).

Solutions (theoretically):
(a) If you don't need your MacOS anymore, you can use chmod/chown to fix these permissions. Of course MacOS won't like that. You also need write access, thus the journal must be disabled.
(b) Use the mount option gid=46 (means plugdev). Unfortunately this option is documented for HFS, but seems to be ignored.

Solutions (should work):
(c) Use your root account which always has unlimited access in Linux.

So something like:
```

sudo rsync --times --recursive --progress --sparse /media/macosx/Users/mario /media/external-drive

```
should copy these files to your external drive. If you use a filesystem supporting permissions such as ext3 on your external drive, these files will belong to the root user, so issue something like:
```

chown mario /media/external-drive/mario

```
to fix this.

If this still doesn't work your disk may be near to its death causing sector errors. Look to the system log.

---

