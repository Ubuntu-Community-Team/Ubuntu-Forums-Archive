---
title: "Lost hdparm.conf file"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by Ramon Lasa on 2006-01-05
I recently enabled DMA on my computer and then edited the hdparm.conf script.  Now when I go to find the hdparm.conf script and edit again, it is empty.  How can I reinstall this hdparm.conf script.  

Thanks in advance for your help.

Ramon

---

### Post by ubuntuuser on 2006-01-05
If you edited the file with gedit there may be a backup called hdparm.conf~. With a bit of luck it still contains your old file. And just in case:```
cp file.name file.name.bak
``` is always a good idea, even more when you edit system files.

---

