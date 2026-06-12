---
title: "Ownership of folders on mounted partition"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Frex on 2007-02-20
Hi,

I use a Ubuntu (Dapper) / WinXP dual boot system, with a separate FAT32 partition for my files. I have mounted this partition to a folder in my user desktop.

Last weekend, I have moved the complete WinXP My Documents folder to this partition, and I resized my partitions: NTFS is now smaller, and FAT32 larger. (I don't know whether this is relevant, but I'd rather give too much information...)

Now, the owner of these folders AND SUBFOLDERS is root, and I have started to give permissions to all users, but the problem is that this has to be done for all the subfolders as well. I don't feel much for such tedious work. Is there an easier/faster way to propagate the same permissions to all underlying folders? Will future subfolders have the correct permissions as well?

Thanks in advance,
Frex

---

### Post by Jussi Kukkonen on 2007-02-20
Not sure if you are trying to do this on the FAT partition. This note is here just in case you are: FAT is a lousy filesystem in many ways, and file permissions/ownership is one of them. It's been a while since I used it, but as far as I remember it just does not support specific file permissions. 


Anyway, this is how you would do it:
```
chmod -R o+rw /path/to/MyDocuments
```
the **-R** option means recursive, **o+rw** gives everyone read and write permission.

---

### Post by Frex on 2007-02-25
Thanks, this worked very well.

The thing now is, that after using FAT32 in WinXP again, these permissions are reset, and I have to use the the chmod-command again.

Is there a way to create a launcher that switches to su and runs the chmod-command again?

I can't stop using WinXP for the time being, I'm afraid :(

Frex

---

