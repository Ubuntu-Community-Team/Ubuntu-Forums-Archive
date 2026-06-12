---
title: "Read and write files to a drive from both kubuntu and windows?"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-07-29
Hello all! 

Messing around with my computer (again) coz its summer and I need to do a bit of spring cleaning! I was just wondering (because it has been irritating me a bit) about my partitions. Looking around the net I see that quite a few people have 3 partitions - Ubuntu, Windows and files (sometimes more). I was wondering whether there was an advntage to this, and whether there was some way (if I did 3 partitions like above) to be able to read and write to the drive from both Kubuntu and Windows.

Thanks for any comments

Olly

---

### Post by jonifen on 2006-07-29
I have not played much with this since installing Kubuntu, but I know that if the files partition is a FAT32 partition (instead of NTFS), you should be able to read/write to it from either operating system.

Kubuntu may be able to support NTFS drives also, but someone else should advise on that :)

---

### Post by Jagot on 2006-07-29
Linux does not support NTFS in general, but there are some experimental methods that you can try, for example:

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

If you need to be able to write to the partition from both Windows and Kubuntu then FAT32 is really the best way to achieve this.

---

### Post by aysiu on 2006-07-29
Read this:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by tartarian on 2006-07-30
Are there any drawbacks to having a FAT32 partition for files?

---

### Post by ProjectGod on 2006-07-30
yeah plenty. for one thing its got security flaws when compared to windows NTFS. furthermore i think it fragments much more than NTFS.  do a google on NTFS vs FAT. those two are usually compared as opposed to EXT2/3 vs FAT.

---

### Post by tartarian on 2006-07-30
Ok, thanks for the help guys! On that tutorial about partitioning (thanks aysiu!!) it mentions Ex2 IFS which allows windows to read EXT file systems so I think I'll give that a try!

---

