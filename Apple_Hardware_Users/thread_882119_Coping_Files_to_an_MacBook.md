---
title: "Coping Files to an MacBook"
date: 2008-08-06
forum: Apple Hardware Users
---

### Post by Killtodie on 2008-08-06
So I got a macbook here that has a password, im doing a data xfer, the client is AWOL and I dont know the password. So I loaded on ubuntu of CD and trying to copy to the HD that way, but the whole mac drive is read only.

How can I get it to copy over? Im trying sudo in terminal, but dont know the copy command. 
Will that work or what do I need to do?

what I got so far is 
```
cp /media/disk[folder name] /media/Macintosh HD
```

what am I missing from that?
right now im tring 
```
cd /media/Macintosh HD
``` but it wont access it

---

### Post by Killtodie on 2008-08-06
ok, now I got something else going

```
 cp /media/disk/Backup '/media/Macintosh HD'
```
That appears to work but when I run it it says "omitting directory '/media/disk/'

???


eh, i think I got it, but when trying to make a new directory it gives me a "read-only file system"

btw, is it read only because its running of the CD or thats how the MacBook is setup?

---

### Post by tiresia on 2008-08-06
To copy a directory you need to specify the option -r
Anyway, I do not understand what are you trying to do.
Do you want just to copy files or you want to access the system?

---

### Post by cyberdork33 on 2008-08-07
yea, I guess I don't understand why you are copying files _to_ an AWOL system... don't you either a) want to backup files or b)fix the broken system?

If you boot OS X in single-user mode, you can access the filesystem without need for Ubuntu. (CMD-S on bootup).

Ubuntu will mount the HFS+ filesystem as readonly because that is a limitation of the linux driver when journaling is enabled (it's great working with proprietary filesystems!). Journaling has to be disabled (done within OS X) in order to gain read/write access to the volume.

---

