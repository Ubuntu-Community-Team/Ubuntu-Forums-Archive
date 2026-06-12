---
title: "Uninstalling Ubuntu"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by lune on 2006-09-20
how would I uninstall ubuntu?

---

### Post by Brunellus on 2006-09-20
> **lune said:**
> how would I uninstall ubuntu?
delete the partition on which you installed it and reformat.

---

### Post by lune on 2006-09-20
is it possible to delete the partition from within Ubuntu? because i have ubuntu dual-booted with win xp. i'm probably going to end up reinstalling ubuntu because i need a fresh install.

---

### Post by shinythings on 2006-09-20
I think you can reformat the partition during the install (but back up your data first!)

---

### Post by Brunellus on 2006-09-20
if you're jsut reinstalling over an existin ubuntu install, simply direct the installer to clobber the relevant partition.  your install will be fresh, and you'll lose any data you put on the old install.

You can't modify a mounted device, so if you just wanted to delete the partition, boot a livecd, run gparted or the partitioner of your choice, and delete the relevant partition(s)

---

### Post by lune on 2006-09-20
thanks for the quick replies. worked well.

---

