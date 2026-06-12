---
title: "Permission problem of files on USB stick? (no permission for groups and others)"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by sundol on 2007-11-12
I want to give a permission for group and others to files in my two USB stick (one is FAT16 and the other one is FAT32).
I tried in many ways but all are failed.

Copying to USB stick (including cp -p), 
creating a file on USB stick directly,
 or 
gzipping, copying and extracting

all of above failed to give any permission for any files in USB stick. Thus, modes of files in my sticks are 600 or 700.

What I really want to do is running a wiki in my USB stick and use it while I shuttle between Linux and Windows. However, deleted permissions in USB simply disables the wiki.

Any suggestions, please?

---

### Post by Nano Geek on 2007-11-12
Try running this in the command-line. I'm on a Windows PC atm, but it should work.```
sudo chmod -hR /media/*nameofusbdrive* *yourusername*
```

---

### Post by CatKiller on 2007-11-12
FAT can't support permissions.

---

### Post by philinux on 2007-11-12
Partition the drive to have a one fat and one ext3 then give the permissions for the ext3 partition.

I'm sure all you need then is a symlink from ext3 to the fat partition where you can store your wiki.

---

### Post by Nano Geek on 2007-11-12
> **CatKiller said:**
> FAT can't support permissions.Hmm. I didn't know that. Thanks

---

### Post by sundol on 2007-11-15
There are no options of "-h" for chmod in Ubuntu 7.10.

---

