---
title: "windows files???"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by tenny56 on 2006-07-10
hey,

ok... i am totally new to this, and as i have now managed to install this OS, i have another question

ready...

i have installed with windows dual booting.  now, is there a way that i can access the files in that partition.  ie. move files over so i can use them through this OS system???

tenny

---

### Post by IYY on 2006-07-10
A common question. The answer is in the FAQ section of the wiki:

[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

There is also a graphical way to do it, through 'disks' and 'gksudo nautilus', but this is much easier.

---

### Post by tenny56 on 2006-07-10
all the more confused i think.

do i want to unmount???

really am soooooo new to this whole thing

sorry

---

### Post by aysiu on 2006-07-10
Post the output of these three terminal commands (just copy and paste the commands and then copy and paste the output): ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

