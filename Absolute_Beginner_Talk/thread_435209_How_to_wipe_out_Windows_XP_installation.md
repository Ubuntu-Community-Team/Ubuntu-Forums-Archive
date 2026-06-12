---
title: "How to wipe out Windows XP installation"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by soho2014 on 2007-05-06
Somehow I managed to install Ubuntu, and it all works, it's a miracle.

But when I try to trash the Windows XP files, it won't let me, saying that I don't have the permission.  How do I delete these files?

I'm a real newbie, since this is my first day with Linux.:guitar:

---

### Post by taurus on 2007-05-06
Why not use gparted (System -> Administration) and format the partition Windows is on.  Convert it to ext3 filesystem and use it as a storage or something.

And if you don't have gparted on your machine, just install it with

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install gparted
```

---

### Post by bobplano on 2007-05-06
do you have ntfs3g? it allows ubuntu to read and write to ntfs, window's native file format(if that's the right term). you also might need to use "sudo rm" or "gksudo nautilus" to get rid of them.
EDIT: if you want to get rid of all the xp stuff you can find gparted on the live install cd and then just get rid of the partitions.

---

