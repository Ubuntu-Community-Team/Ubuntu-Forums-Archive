---
title: "Quick Question: Disk Space in Ubuntu"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by peddy on 2007-11-05
Whenever I log in, a balloon tells me that '/' is 100% full. This is confirmed by looking at system monitor> file systems. Is there any way to reduce the amount of stuff in /, or even a easy way to resize it? (although I would prefer the former)

Thanks
Peddy

---

### Post by lyndaj70 on 2007-11-05
Hello!
Try going to synaptic, then go to settings>preferences>files and delete all cached files.  That should help some.  Then if your /home directory is on the same disk remove some of your files, you could also use synaptic to uninstall some software....

Do you have any room to expand into?  This is only a temporary fix....
~Lynda

---

### Post by Arthur Archnix on 2007-11-05
Read this [thread]("http://ubuntuforums.org/showthread.php?t=140920&highlight=locale+purge").

---

### Post by peddy on 2007-11-06
I have a *lot* of free space, I just don't know how to resize the partitions. Using gparted in a live CD does not work for me. I have cleaned the cache. Any more ideas?

---

### Post by Adramelech on 2007-11-06
gparted is a pain now, everytime it finish doing something, it mounts the partition and then complains the partition is mounted! it can drive you crazy, believe me. Try doing only 1 operation at a time.

---

