---
title: "Accessing a Windows drive (was: y wont any one help me?????)"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by sid28 on 2006-09-24
how cani access my files on windows? on my c drive or d drive?

---

### Post by avidsensei on 2006-09-24
is it an ntfs drive?

---

### Post by lonce on 2006-09-24
Linux will only access a Fat32 drive.  If your windows drive is NTFS then you are out of luck.

---

### Post by Houman on 2006-09-24
Linux can read NTFS, it has been able to for a long while, 
check out the dapper guide here.[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

Houman

---

### Post by DrMilo on 2006-09-24
> **lonce said:**
> Linux will only access a Fat32 drive.  If your windows drive is NTFS then you are out of luck.

Not quite. The link below is a simple way to get access to the files, it is read only but that's better than nothing. Other ways of doing it are rather hard and experimental.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-f59428cd4d1c1b020a3a06bae2242b3d7f45a06d](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-f59428cd4d1c1b020a3a06bae2242b3d7f45a06d)

---

### Post by sawjew on 2006-09-24
You could try this for read/write to NTFS [http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")

Or this for read only to NTFS (safer) ["http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only"]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

Or this for read/write to FAT32 [http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")

I personally have not had much success with read/write to NTFS but no problems with read only NTFS and read/write to FAT32.  I have all my documents on a shared FAT32 partition on my desktop and on a shared ext3 partition on my laptop. 

Windows can read/write to ext3 using this [http://www.fs-driver.org/]("http://www.fs-driver.org/")

You can put all your documents on ext3 and then redirect My Documents to it.

---

### Post by Brunellus on 2006-09-24
Thread title changed to better reflect nature of help request.  In the future, please use the thread title to sum up briefly the TYPE of problem you need help with.  This allows the users who know how to help you to know that they can help you. 

This is a COMMUNITY SUPPORT FORUM, *not* a paid help desk.  So please do not abuse the patience or goodwill of users here by posting "y wont any one help me??" as your thread title.  Your requests for help will be more successful if you treat the community with respect and let people know exactly what your problems are, rather than simply demanding attention.

Your specific problem can be solved by following the directions on [this page](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28Windows%29)

---

### Post by bodhi.zazen on 2006-09-24
> **Brunellus said:**
> Thread title changed to better reflect nature of help request.  In the future, please use the thread title to sum up briefly the TYPE of problem you need help with.  This allows the users who know how to help you to know that they can help you. 

This is a COMMUNITY SUPPORT FORUM, *not* a paid help desk.  So please do not abuse the patience or goodwill of users here by posting "y wont any one help me??" as your thread title.  Your requests for help will be more successful if you treat the community with respect and let people know exactly what your problems are, rather than simply demanding attention.

Your specific problem can be solved by following the directions on [this page](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28Windows%29)

Brunellus: Thank you I have noticed a few instances where you have re-named and advised posters today. Your clarification is helpful and your advice is on target.

---

