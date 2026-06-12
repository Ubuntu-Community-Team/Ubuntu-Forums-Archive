---
title: "Can write to one hfsplus partition, but not another"
date: 2006-08-23
forum: Apple PPC Users
---

### Post by calum on 2006-08-23
Gah, this is driving me nuts :)

I have two unjournalled, HFS+ partitions on an external drive.  Their fstab entries are identical:

[FONT="Courier New"]/dev/sdb2 /mnt/p2 hfsplus rw,users 0 0
/dev/sdb3 /mnt/p3 hfsplus rw,users 0 0
[/FONT]

as are their mtab entries once they're mounted:

[FONT="Courier New"]/dev/sdb2 /mnt/p2 hfsplus rw,noexec,nosuid,nodev 0 0
/dev/sdb3 /mnt/p3 hfsplus rw,noexec,nosuid,nodev 0 0
[/FONT]

yet I can write to /mnt/p2, but not to /mnt/p3.  

If I do an ls -l on /mnt, I see a difference:

[FONT="Courier New"]drwxr-xr-x root root   18 2006-08-24 01:21 p2
drwxrwxrwx root admin 39 2006-08-22 15:19 p3[/FONT]

Even if I delete the /mnt/p3 and recreate it with the same permissions as p2, it goes back to 777/root/admin whenever I mount the partition. with the 2006-08-22 datestamp.  So I assume it must be getting all that information from the external drive partition itself somehow.

The only difference between the partitions is that p3 is a bootable (OSX) partition, while p2 just contains regular data.  Would that cause this issue?  If not, what's going on, and how can I fix it?

---

