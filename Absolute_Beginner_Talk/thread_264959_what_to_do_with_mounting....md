---
title: "what to do with mounting..."
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by Sterbik on 2006-09-25
when i install ubuntu, it requries to mount some files, such as "root" "swap" etc. What does mean. I also looked deeper in this website for an answer, but nothing... I don't know what to mount, and where, because there are lot of choices...

---

### Post by CatKiller on 2006-09-25
I think it's asking for a "mount point". In the Linux filesystem, you can have files from lots of different places - multiple hard drives, cd-rom drives, and so on - all included in the filesystem heirarchy. The mount point is where in the filesystem you put these different data sources.

Mounting is the act of taking a data source and attaching it to the filesystem.

None of this is hugely necessary to actually getting Ubuntu installed, though. By default, I believe that the installer creates two partitions - one for actual files and one for swap space. You should only encounter the possibility of making multiple partitions for different mount points if you've gone for some Advanced Option. As a new user to the Linux world, you should probably work your way up to that ;)

---

