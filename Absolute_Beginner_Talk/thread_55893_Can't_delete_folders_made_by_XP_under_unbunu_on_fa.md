---
title: "Can't delete folders made by XP under unbunu on fat32 partition"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by Tristan9669 on 2005-08-10
I created a fat32 partition and I moved some folders in it with XP and when I'm under ubuntu it wont let me delete the folders or its contents. It also has a lock icon on the folders made by xp

---

### Post by varunus on 2005-08-10
How are you mounting the FAT32 partition?  If it is in your fstab, you need to make sure it looks like this:
```
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
```
The umask=000 should let all users read/write.  If this doesn't work, try the following instead:

```
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000,uid=1000   0       0
```
This has the side effect of making it show up in your "computer" place also.

---

### Post by Tristan9669 on 2005-08-10
ill try this

---

### Post by Tristan9669 on 2005-08-10
They both don't work, still same problem.

---

### Post by poofyhairguy on 2005-08-10
[QUOTE=Tristan9669]They both don't work, still same problem.[/QUOTE]

Can a super nautilus do it? try this command in a regualr terminal:

> gksudo nautilus

(please be careful with that.....its REALLY powerful)

---

### Post by Tristan9669 on 2005-08-10
I got it to work, I just went under xp deleted the files and copy them back over with ubuntu and now it lets me delete or whatevr

---

### Post by alquimista on 2005-08-10
Hi,
I have just the same problem; even for files cretaed under Kubuntu on a FAT32 partition. FOr examle, under user gnajar I create and write files, and in Kubuntu I can move, rename, write on them... but I can't delete them from Konkeror! I have to do it being root on a terminal.
How can I fix this problem??


Thanx!
Guillermo

---

