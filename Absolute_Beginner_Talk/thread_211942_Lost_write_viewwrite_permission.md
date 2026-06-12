---
title: "Lost write view/write permission"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Kuraboy on 2006-07-09
Hi!

I was just trying to make a backup and saved the backup file to hda5, which is a FAT32 harddrive...

the backup went succesfully... but the problem is later when I tryed to navigate to hda5 it said I dont have permission to view it. So I tryed to use chmod to solve it.

now I can see and execute the files, but I dont know how to be able to write ? Before the backup I was able to write to the drive... something went wrong please help!

here is the permission for hda5 [after that I have tryed several times]:
```
drwxrwx--- 22 root plugdev 32768 2006-07-09 10:19 hda5
```

thnx.

'''''
EDIT, thnx anyway... somehow when I closed bash it worked... seems like it didnt update properly?! Thnx and sorry for me cluttering the furoms ^_^;;;

---

### Post by simonn on 2006-07-09
fat partitions are not capable of storing permission information.

Permissions are dealt with when the partition is mounted through mount parameters.

Read the "Mount options for fat" section in man mount, particularily the uid, gid and ?mask parameters.

---

