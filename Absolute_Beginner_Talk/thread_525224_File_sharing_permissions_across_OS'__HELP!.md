---
title: "File sharing permissions across OS'???  HELP!"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by myk.dinis on 2007-08-14
I have 3 disks...

1. Xp - NTFS
2. "Shared" - Fat32 - It has "Documents and Settings" on it...
3a. Ubuntu - ext3
3b. SWAP
3c. /home

--------------

I want to move the contents of my /home/Share folder thats on my partition to 2:\Documents and Settings\All Users\Documents (the windows shared folder)...

I'm running out of room on 3c and there is only 3 gigs out of 40 being used on 2

Does anyone know how I can do this?  I would also like to be able to make /home/Share a logical link to that other folder on the other drive?

Could someone help me?

thank you...

---

### Post by nexu56 on 2007-08-14
You just need to mount the windows drive (2):
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite]("http://http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite")

Then you can use your windows disk in ubuntu.

---

### Post by 1/0 on 2007-08-14
You could make a symlink by:

```
ln -s
```

More info on in the man:

```
man ln
```

---

