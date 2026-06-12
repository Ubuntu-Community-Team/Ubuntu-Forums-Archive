---
title: "Write to FAT 32 filesystem ?"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-10-14
Is there a problem with this ? I need to transfer some files to a fat32 partition..... I know that it's experimental with NTFS. Thanks :)

---

### Post by luckylucky on 2006-10-14
I would be happy to discuss fat32 filesystems, however your post is unclear.  Could you please clarify what your question is?  Thanks.

---

### Post by Drakkor on 2006-10-14
Ok,what I want to do is to cut a file from ext3 and paste it in fat32....
in other words,writng to the fat32 partition, would it be accesible in both 
Ubuntu and XP ?  Thanks :)

---

### Post by Frak on 2006-10-14
That wouldn't make much since because, XP uses NTFS not FAT32, and you can write to it just don't expect it to always work, it's still experimental. I'll find a wiki to this and post it here.

---

### Post by jimrz on 2006-10-14
> **Drakkor said:**
> Ok,what I want to do is to cut a file from ext3 and paste it in fat32....
in other words,writng to the fat32 partition, would it be accesible in both 
Ubuntu and XP ?  Thanks :)

yes you can access FAT32 read/write from both win and ubuntu

---

### Post by Drakkor on 2006-10-14
Thanks,guys, I will try it out tomorrow,and post back ! :p

---

### Post by Frak on 2006-10-14
Reading and writing from FAT32 is almost perfect compared to read/write NTFS filesystem.

---

### Post by givré on 2006-10-14
Little adjustment :
read/write on FAT32 *is* perfect
read/write on NTFS is almost perfect

---

### Post by jenny on 2006-10-14
I don't think there's any issue. One can have an easy access of  FAT32 read/write from both windows Xp and ubuntu !

---

### Post by jorn on 2006-10-14
Max filesize in fat32 is 4GB.

---

### Post by xmastree on 2006-10-14
> **Drakkor said:**
> Is there a problem with this ? I need to transfer some files to a fat32 partition..... 
Assuming you already have the FAT32 partition somewhere on the system, just mount it somewhere, with the correct permissions, and it'll be just fine.

Here's the guide explaining how to mount it:
[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

---

