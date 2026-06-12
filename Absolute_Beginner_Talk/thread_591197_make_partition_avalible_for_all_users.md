---
title: "make partition avalible for all users"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by nalleballe on 2007-10-25
I have a FAT partition with music (between the systems) and i would like this partition avalible by me all the time without superuser. Is there any commandolines you can give me for this? The strangest thing is that when i log in to it from windows i cant see the files.... They are gone. :mad:

---

### Post by Paqman on 2007-10-25
To permanently mount a partition (if it wasn't done during installation) you need to add an entry to a file called /etc/fstab. Be careful with that file though, read this first:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by nalleballe on 2007-10-25
it cant even find the disc... its not even a part of fstab or anything. (its called hda5 and its FAT. its visible in root desktop but not in admin) what to do now? thanx a bunch

---

### Post by taurus on 2007-10-25
Open a terminal and edit /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hda5   /media/hda5   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hda5
sudo mount -a
df -h
```
Now, you can access that partition from /media/hda5 and it will be mounted automatically each time you boot Ubuntu.

---

### Post by nalleballe on 2007-10-25
taurus u saved a lost ubuntu-user today and his name is nalleballe :guitar:

---

