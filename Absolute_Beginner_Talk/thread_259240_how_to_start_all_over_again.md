---
title: "how to start all over again?"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-09-17
Well, I have tried everything to get my system working again but I am still having problem with booting Windows etc. so I want to start afresh so how do I clean my hard drive so I can reinstall Windows and Ubuntu?

Russty

---

### Post by steve.horsley on 2006-09-17
You want to wipe out both Ubuntu and windows? If so, maybe the easiest is to boot up the Ubuntu live installer CD, then use gparted to delete all the partitions on the hard disk. Then boot the Windows installer. If the windows installer allows you to only use part of the disk, then that will save the Ubuntu installer trying to shrink the Windows partition later on.

---

### Post by Russty of Oz on 2006-09-17
gparted wont let me delete the ubuntu partition, it has a lock next to it.  In fact even Windows has a lock next to it.  When I click unmount it says I have to do it manually.  How do I unmount a partition?

Russty

---

### Post by steve.horsley on 2006-09-17
That's why I say to boot the installer live CD. You can't delete a mounted partition, so you can't delete the installed Ubuntu from within itself. But the live CD runs Ubuntu without mounting any hard disk partitions, so you can trash the hard disk without restrictions.

---

### Post by Russty of Oz on 2006-09-17
OK, now I understand.

Russty

---

