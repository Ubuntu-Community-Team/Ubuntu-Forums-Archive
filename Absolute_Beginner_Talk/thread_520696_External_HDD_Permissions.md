---
title: "External HDD Permissions"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by kevin11951 on 2007-08-08
I want to use and external hdd i have, to move files between my ubuntu laptop, and my vista desktop... i wondering what the best "universal" file system is, that all os's can read, or at least as close as i can get!

---

### Post by Rocket2DMn on 2007-08-08
FAT32 is read natively by Windows and Linux, but I hate the 4GB file size limit.  This is the best way, though.
Many of us who dual boot use the NTFS file system that Windows XP/Vista sets up when it formats a drive.  With the program ntfs-3g you are able to read/write to NTFS partitions from Ubuntu (since it finally has a stable release).  This is the best alternative to FAT32.
There is a driver at [http://www.fs-driver.org](http://www.fs-driver.org) that allows Windows to read ext2/3 file systems that linux sets up by default, but some people have found that it can corrupt the file system (perhaps because using this driver in Windows mounts an ext3 drive as ext2).

---

### Post by kevin11951 on 2007-08-08
when i first wrote this thread it was "supposed" to be about permissions, so sorry about the title, but while im on the subject, if i use chmod, how would i make it so the permissions are also "universal"?

---

### Post by Inxsible on 2007-08-08
> **kevin11951 said:**
> when i first wrote this thread it was "supposed" to be about permissions, so sorry about the title, but while im on the subject, if i use chmod, how would i make it so the permissions are also "universal"?

```
sudo chmod 777 /path
``` This will give read write and execute permissions to everyone on that folder. You can use the -R option to recursively give same permissions for all the files and folders within this folder. have a look at the man pages to get more info.

---

### Post by Rocket2DMn on 2007-08-08
Using NTFS or FAT32, when you mount the drive, you can set it to mount so that everybody can access the files on it.
Here are good places to start: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

