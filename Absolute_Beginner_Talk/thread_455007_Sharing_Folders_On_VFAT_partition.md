---
title: "Sharing Folders On VFAT partition"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Nommy on 2007-05-26
Hi Everyone,
This is my first mail on this forum as I have recently joined it. I have recently installed Ubuntu 5.10 on my Server machine. Everything is working perfectly well like Folder Sharing using SAMBA connectivity with my WindowsXP.

The problem that i am facing is that any Folder created on Fat32 partition cannot be shared except with root user. When I tried to change the user from "root" using folder properties, I get a message "User Cannot be Chaged" and same thing happens when changing the Folder's Group. This does not happen if I share a folder on ext3 partition.

Actually I have opted Ubuntu 5.10 as server in my office. On this Server I two have 20GB Fat32 partition. I want to create 4 folders on each partition and share each folder individually with a single user such that each user can copy his backup unto his folder only and cannot access other user folders.

Using previous posts on this forum I have acheived a lot in setting up my server machine except with this issue only. My Server machine is intel P-III.

Please help me with this issue. 

Thanking you,

Nommy.

---

### Post by nonewmsgs on 2007-05-26
in a terminal try
sudo nautilus 
and then change permissions.

also welcome to the forums!

---

### Post by psusi on 2007-05-26
You can not change permissions on fat partitions because the fat filesystem does not store permissions and ownership.  You need to edit your /etc/fstab line to include a uid= option to specify who should appear to own all of the files.

---

