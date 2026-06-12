---
title: "[help] fstab"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by pcandpc on 2007-07-02
Hi,

I used to have /home mounted on a separate hard drive
as reiserfs, but I have changed the file type to ntfs as
I want to share this drive with windows.

Currently, I have the following in /etc/fstab for this drive:
<file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hdd1    /home        ntfs    rw,noauto    0    0

This appears to work, but what would the most optimal
values for options, dump, and pass for this ntfs drive?

Thanks.

---

### Post by Rocket2DMn on 2007-07-02
I don't believe you can just change the file system in fstab and make it so - the drive has to be formatted for that.  You can go to [www.fs-driver.org](www.fs-driver.org) and get a little addon to windows that allows it to read/write ext2 and ext3 drives

---

### Post by Bothered on 2007-07-02
I would leave the home partition as reiserfs, and use the add-on mentioned in the previous post in Windows. ntfs doesn't support file permissions.

Btw, I personally use ntfs-3g for ntfs partitions.

---

### Post by pcandpc on 2007-07-02
Thanks.
 
Well, I formated /dev/hdd1 as ntfs from ubuntu.
 
Now, accessing this drive from windows shows
the drive as empty.
 
By the way, the information on the link seems
to be appropriate for accessing ext2/3 filesystems, 
not reiserfs from windows.
 
So, is there a tool to access reserfs fully (read/write)
from windows?

---

### Post by Bothered on 2007-07-03
Formatting a partition deletes all data on it. You'll need to restore it from a backup.

---

### Post by meborc on 2007-07-03
> **Bothered said:**
> Formatting a partition deletes all data on it. You'll need to restore it from a backup.

i think that was the goal...

i would install ntfs-config package and set up the ntfs partition from it's gui... very simple and effective

```
sudo apt-get install ntfs-config
```

---

