---
title: "Filesystem full for unknown reason"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by detroit/zero on 2008-01-20
I just installed Gutsy on my girlfriends laptop. 

When I wasn't looking, she decided to start migrating files and such from her Windows drive into her Ubuntu partition. She thought it would be a good idea to, in one fell swoop, copy a 22GB folder containing all her documents, movies, music, etc.. into her drive.

Because of the way the disk is partitioned, that file copy all but filled up her Ubuntu partition and it started sending the "disk is full" warnings. It took some doing, but I managed to move the files to some reserve space elsewhere on the hard-disk. I then deleted (not *move to trash* - but the *delete* option) the 22GB folder, but Ubuntu still says that the disk is full. I can't find what's eating up all the space.

Basically, I have a nearly 30GB partition that has only 7.5GB of actual data on it, but still reads as being full. I don't see anything in Nautilus (or a root-nautilus window), and nothing shows up in the disk-usage-analyzer; disk-analyzer actually says something completely different and that the file system is only 74% used..

What is eating up all this space? How can I find it and erase it?

---

### Post by Sef on 2008-01-20
Two possiblities:

1) Click on the Trash Can > View > Show Hidden Files.   Maybe hidden files there.

2) Corruption of some of the data.  Go into properties and check the file sizes.

---

### Post by detroit/zero on 2008-01-20
I did the properties thing already and looked at everything in her home directory; I didn't see anything that was out of place.

I checked the trashcan on your advice and didn't see anything in it, even when looking at hidden files.

Here is a root terminal output of ls -l in her filesystem:
```
 root@XXXXXXX:/# ls -l
total 92
drwxr-xr-x   2 root root  4096 2007-11-20 23:46 bin
drwxr-xr-x   3 root root  4096 2008-01-19 20:36 boot
lrwxrwxrwx   1 root root    11 2007-11-20 20:52 cdrom -> media/cdrom
drwxr-xr-x  13 root root 14000 2008-01-20 16:30 dev
drwxr-xr-x 124 root root 12288 2008-01-20 16:42 etc
drwxr-xr-x   4 root root  4096 2008-01-20 01:48 home
drwxr-xr-x   2 root root  4096 2007-10-16 01:17 initrd
lrwxrwxrwx   1 root root    33 2007-11-20 23:45 initrd.img -> boot/initrd.img-2.6.22-14-generic
drwxr-xr-x  18 root root 12288 2008-01-19 21:24 lib
drwx------   2 root root 16384 2007-11-20 20:52 lost+found
drwxr-xr-x   6 root root  4096 2008-01-20 16:27 media
drwxr-xr-x   2 root root  4096 2007-10-08 12:47 mnt
drwxr-xr-x   4 root root  4096 2008-01-19 21:57 opt
dr-xr-xr-x 141 root root     0 2008-01-20 17:26 proc
drwxr-xr-x  18 root root  4096 2008-01-20 16:45 root
drwxr-xr-x   2 root root  4096 2008-01-19 20:32 sbin
drwxr-xr-x   2 root root  4096 2007-10-16 01:17 srv
drwxr-xr-x  12 root root     0 2008-01-20 17:26 sys
drwxrwxrwt  14 root root  4096 2008-01-20 17:22 tmp
drwxr-xr-x  12 root root  4096 2008-01-19 21:16 usr
drwxr-xr-x  15 root root  4096 2007-10-16 01:31 var
lrwxrwxrwx   1 root root    30 2007-11-20 23:45 vmlinuz -> boot/vmlinuz-2.6.22-14-generic
root@XXXXXXX:/#
```

---

### Post by ajgreeny on 2008-01-20
What is the output of ```
df -m
```It may still tell you that the filesystem is full, but it's worth looking.  Also use the Accessories>Disk Usage Analyser which may tell you where the space is being used.

---

### Post by detroit/zero on 2008-01-20
```
XXXXXXX:~$ df -m
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda5                28159     26459       270  99% /
varrun                     248         1       248   1% /var/run
varlock                    248         0       248   0% /var/lock
udev                       248         1       248   1% /dev
devshm                     248         0       248   0% /dev/shm
lrm                        248        34       214  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1                 3985      3310       675  84% /media/sda1
```

Let me explain my findings with Disk Usage Analyzer a little better:

According to it, the disk is not full. It shows 2.3 GB of 30 or so GB being free, but when you add up the largest files in the drive, it doesn't come out anywhere close to 30GB. For the life of me, I can't understand why there is any more than 7 or 8 or maybe 10GB at the most inside this file system.

It seems to me that the other volumes on the hard disk are being mounted (inside /media, obviously) and that the sizes of these volumes are counting against the free space available inside /

These volumes are not mounted in this screenshot, but you can still see that the numbers listed for file sizes do not jive with the stated free space in the status bar:
[http://img182.imageshack.us/img182/3289/screenshotvncprincessprpm7.png](http://img182.imageshack.us/img182/3289/screenshotvncprincessprpm7.png)

---

