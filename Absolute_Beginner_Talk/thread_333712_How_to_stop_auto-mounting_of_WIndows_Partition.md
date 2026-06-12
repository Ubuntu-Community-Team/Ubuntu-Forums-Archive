---
title: "How to stop auto-mounting of WIndows Partition?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by MindRiot on 2007-01-07
How do I prevent Linux from automatically mounting my WIndows (/media/hda1) partition when Linux boots?

---

### Post by taurus on 2007-01-07
If you don't want to mount /dev/hda1, then just remove that entry in /etc/fstab.

Applications -> Accessories -> Terminal
```
gksudo  gedit  /etc/fstab
```

---

### Post by MindRiot on 2007-01-07
O.K. Thanks. 

I'll see if placing a # in front of the line will do the same thing.  That way, if I want to mount the partition in the future,  the info will still be there.   :)

---

### Post by chesman on 2007-01-07
Thats what i did and worked like a charm

---

### Post by taurus on 2007-01-07
> **MindRiot said:**
> O.K. Thanks. 

I'll see if placing a # in front of the line will do the same thing.  That way, if I want to mount the partition in the future,  the info will still be there.   :)

Yes, a # behaves like a comment so if you don't want to delete it, comment it out.

---

### Post by hal10000 on 2007-01-08
If you don't want to mount it at boot time, but at any other time you want, then make an entry in your /etc/fstab like
```

/dev/hda1       /media/hda1     ntfs    noauto,user,nls=utf8,umask=007,gid=46 0       1

```
you don't need to change the nls,umask and gid entry in your fstab, but change the (presumed) defaults entry to noauto,user.

This gives you the chance to mount it as normal user at any time you like.

---

