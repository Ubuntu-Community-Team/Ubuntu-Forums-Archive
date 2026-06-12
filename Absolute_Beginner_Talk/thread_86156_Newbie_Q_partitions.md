---
title: "Newbie Q: partitions"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by goyan on 2005-11-04
Hi, I just install my first Linux/Ubuntu. I have two 120GB HDDs, I assigned the first one to be "/" and the second one to be "/home".  I've set up my samba server to share a folder named "LocalShare" in my home directory (i.e. "/homt/goyan/LocalShare". I plan to put all my movies, tv series, mp3, ebooks in that directory. What will happen if the content in the LocalShare folder gets more than 120GB?

Goyan

---

### Post by Ampersand on 2005-11-04
You shouldn't need more than about 7 or 8Gb for the filesystem, so you could make another folder on your first hard drive and share that one as well.

---

### Post by goyan on 2005-11-04
So, the "home" directory will not automatically include some of free spaces on the first hdd?

---

### Post by Ampersand on 2005-11-04
No, the home directory would be similar to the d:\ drive on a windows computer with 2 hard drives.

---

### Post by ofek on 2005-11-04
[QUOTE=goyan]So, the "home" directory will not automatically include some of free spaces on the first hdd?[/QUOTE]
Damn that could be so cool if when u get to the 120gb a window will popup asking if u want to use free space from the other 120gb drive but im not even sure that mechanicly possible.

---

### Post by LHZ on 2005-11-05
I'm pretty sure you could make like a 100 GB partition on the Main Drive (leaving 20 GB for Ubuntu), and then use LVM (Logical Volume Manager) to treat the 100 GB and the 120 GB partitions as a single 220 GB partition. I've never done it though, so you'll have to google around a bit or ask someone more experienced.

---

### Post by Bloged on 2005-11-05
Isn't it simple possible to emulate this with an symlink? Then you enter a directory on the first disk and end up on the other?

Grtz,

Bloged

P.s. this answer came from a Linux-n00b :rolleyes:

---

