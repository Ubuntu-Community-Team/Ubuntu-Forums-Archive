---
title: "R/W Permissions on munted Ext3 drive"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by Aberrix on 2006-10-07
Alright, So I have a 250GB storage drive that I use for nothing but files (audio, video, etc). I figured out how to get it mounted this morning bit I only have READ access and I want READ/WRITE. I have searched but mostly everything is for r/w on a windows (ntfs/fat) drive. This is for a Ext3 drive, I know I am missing something small... please help.

this is what my /etc/fstab looks like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/storage  ext3    defaults,errors=remount-ro 0       1
```

sda1 /media/storage is the drive I wish to have rw acess on. Thanks in advance.

---

### Post by zappa on 2006-10-07
sudo chown enteryourloginhere -rf /media/storage
should do the trick

---

### Post by Aberrix on 2006-10-07
I get the following error:

```
aberrix@haddax:~$ sudo chown aberrix -rf /media/storage
chown: invalid option -- r
Try `chown --help' for more information.
```

---

### Post by kidders on 2006-10-07
> **zappa said:**
> sudo chown enteryourloginhere -rf /media/storage
should do the trick

Yep... either that or the "errors=remount-ro" is happening. Is your filesystem damaged?

---

### Post by Aberrix on 2006-10-07
> **kidders said:**
> Is your filesystem damaged?

I hope not, how would I check?

---

### Post by kidders on 2006-10-07
Your dmesg will probably say something about anything odd that happened while it was mounting. If not, you can double-check by dismounting it again and running fsck on it.

I only mentioned corruption because mounting something read-only is a pretty sensible way to handle a damaged filesystem. That way, you can take a look at it without making things any worse! On the other hand, if doing an **ls -l /media/storage** shows you lots of stuff that you don't have permission to write to, zappa's solution should do the trick nicely.

---

### Post by zappa on 2006-10-07
Well, indeed, let's 
sudo umount /dev/sda1
then
sudo gedit /etc/fstab 
change the last line in 
/dev/sda1       /media/storage  ext3    defaults 0 2
sudo mount -a
then
sudo chown enteryourloginhere -R /media/storage
(Nothing wrong should have happened since -r is wrong, has to be -R)

---

### Post by Aberrix on 2006-10-07
> **kidders said:**
> Your dmesg will probably say something about anything odd that happened while it was mounting. If not, you can double-check by dismounting it again and running fsck on it.

I only mentioned corruption because mounting something read-only is a pretty sensible way to handle a damaged filesystem. That way, you can take a look at it without making things any worse!

```

sudo fsck /dev/sda1
Password:
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Storage: clean, 32340/30539776 files, 21041011/61049000 blocks
```

everything looks good as far as I can see?

[QUOTE=kidders;1590494On the other hand, if doing an **ls -l /media/storage** shows you lots of stuff that you don't have permission to write to, zappa's solution should do the trick nicely.[/quote]

```
drwxr-xr-x  9 root root  4096 2006-10-06 16:29 Applications
drwxr-xr-x  5 root root  4096 2006-10-06 16:39 Audio
drwxr-xr-x  8 root root  4096 2006-10-06 16:56 Documents
drwx------  2 root root 16384 2006-10-05 12:30 lost+found
drwxr-xr-x 22 root root  4096 2006-10-06 16:59 Photos
drwxr-xr-x  2 root root  4096 2006-10-06 18:26 Recycled
```

looks to me like a permissions problem? but when I try what zappa said I get the following message:
```
aberrix@haddax:~$ sudo chown aberrix -rf /media/storage
chown: invalid option -- r
Try `chown --help' for more information.
```

what am I doing wrong?

---

### Post by Aberrix on 2006-10-07
> **zappa said:**
> Well, indeed, let's 
sudo umount /dev/sda1
then
sudo gedit /etc/fstab 
change the last line in 
/dev/sda1       /media/storage  ext3    defaults 0 2
sudo mount -a
then
sudo chown enteryourloginhere -R /media/storage
(Nothing wrong should have happened since -r is wrong, has to be -R)

that worked! thank you so much! should I put back in the ```
errors=remount-ro
```or just leave it as it is? thanks again!

---

### Post by zappa on 2006-10-07
ro stands for read only, so if you want to store some more media, i'd leave it as it is ;)

---

### Post by Aberrix on 2006-10-07
> **zappa said:**
> ro stands for read only, so if you want to store some more media, i'd leave it as it is ;)

I get it now ;) thanks again!

---

### Post by kidders on 2006-10-07
If I were you I'd put it back as a convenience in the event of a problem. It won't have any effect during normal operation.

---

### Post by zappa on 2006-10-07
I just learned a lot about errors=remount-ro
Thanks kidders. 
(Question, what is seen as an error? bad block devices?)

---

### Post by kidders on 2006-10-07
I'm not 100% certain about that. I imagine "error" refers to anything at all that could go wrong. My understanding is that adding an **errors=remount-ro** directive will get mount to reattempt a failed mount in a way that might be more likely to succeed. It's not terribly important.

---

### Post by zappa on 2006-10-09
FYI: I've been google-ing. Apparently it's when errors are find while performing a check, ie the one every 30 days.

---

### Post by Karl Norway on 2007-02-04
Try to using -R for chown command

like sudo chown username -R /media/disknumder

-R stand for Recursive and means that you will get read/write acess to all files and folders under that point

---

