---
title: "How do I apply a patch?"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by Kimm on 2006-10-03
I didnt know where to put this... so I put it here.

How do I aply patch xxx.diff to file xxx.tar.gz/bz2

Do I extract it first? or what do I do? :confused:

---

### Post by tseliot on 2006-10-03
I have moved this thread to a more appropriate section

---

### Post by Kimm on 2006-10-05
/bump

Doesnt anyone know??! :confused:

---

### Post by jaboua on 2006-10-05
It's been a while since I patched something, but IIRC it's like:
1) extract the archive
2) cd into the directory of the source
3) run "patch -p1 </location/of/patch.diff"

For example if you save a patch.diff and source-1.2.tar.gz in /home/username/:

tar -zxf source-1.2.tar.gz
cd source-1.2
patch -p1 </home/username/patch.diff

---

