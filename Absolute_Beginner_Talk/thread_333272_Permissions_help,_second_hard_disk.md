---
title: "Permissions help, second hard disk"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by japan on 2007-01-07
Near-total Linux newbie here, I got Dapper installed on my desktop and my wireless working with minimal problems, but I'm now having an issue with my second hard disk.

I'm dual booting with Windows XP, so I have Dapper and Windows sharing my first hard disk (hdb1 (windows) and hdb2 (Ubuntu)). Before I installed, I moved all my files to a second hard disk (formatted as FAT32 and split into two partitions, hdd1 and hdd2. Mounts as /media/hdd1 and /media/hdd2) primarily to make life easier if I have to share files between the two OSes.

However, I can't save directly to either partition of hdd, because I don't have permission to do so. They're currently set as drwxrwx---, the owner is root and the group is plugdev. As far as I understand it, this means that the user "root" and any members of the group "plugdev" have unfettered access, and no-one else can access it at all.

My question is; what is the correct way to set the permissions such that my user can read and write to the drive? The "Users and Groups" tool in Sytem -> Administration says my username is part of the "plugdev" group, but if I try to save to the drive, an error message appears telling me I don't have write permissions.

Sorry if I've rambled a bit, thanks in advance for any help.

---

### Post by teaker1s on 2007-01-07
could it be that the hard drive has mounted read only? if so it needs mounting read/write

take a look at this site it explains mounting and many other topics
[http://www.ubuntuguide.org/]("http://www.ubuntuguide.org/")

---

