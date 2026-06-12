---
title: "Change owner"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by chr_84 on 2006-06-26
Hi!

I've just formatted my second harddrive (fat32) so I can access it from both windows and linux. The problem is that I have to use the terminal and sudo to do anything on it, because "root" is set to owner.

I've tried to change the owner with the commando
"sudo chown -R username:username /media/hdd1"

but I keep getting an error message telling me that the operation is forbidden.

What shall I do?

---

### Post by frodon on 2006-06-26
Here are the instructions to mount your FAT32 partition with read/write access for all users :
[http://doc.gwos.org/index.php/DapperGuide#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://doc.gwos.org/index.php/DapperGuide#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)
On the other hand the FAT32 file system don't support unix rights and ownership that's why the chown, chmod, ... don't work with this file system

---

