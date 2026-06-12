---
title: "Trouble coordinating permissions with mount (bind)"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by deadimp on 2007-03-18
I've set up a fat32 partition on my secondary drive (/dev/hdb1), aside from the ntfs partition (/dev/hdb2).
I've created my directory to mount the drive as /media/www, and mounted it with root permissions (using "su" to go into root bash).
Next, I create a folder that's higher up, /www, just 'cause I'm lazy in typing, and bind it to the other directory.
Problem is, when browsing the partition /dev/hdb1 as a common user (deadimp), I only have read-style permissions (Access files). I can't create files / directories. When I browse the partition as root, I can do whatever.
I've tried changing the permissions, but when the partition is mounted, I'm unable to change anything. When it's unmounted, I can change the permissions as with a normal file.
This concerns me because this is my 'sync' partition between Windows and Ubuntu, with my common files on it (http docs, MySQL data, Thunderbird, Firefox settings, etc). I want to be able to run Firefox and Thunderbird as deadimp without any problems of read/write access, recreating drafts on Mail, etc.

Amazingly (well, not really since they're cross-platform), Thunderbird and Firefox read the data well, except that Firefox can't read the theme for some reason (it's on default even though I've selected HaikuFox).

---

### Post by giftnudel on 2007-03-19
Hi,

please refer to [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")

If you have any other questions, please ask

giftnudel

---

