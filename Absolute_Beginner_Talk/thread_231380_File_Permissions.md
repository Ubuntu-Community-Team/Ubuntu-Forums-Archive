---
title: "File Permissions"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Paul41 on 2006-08-07
I am trying to understand how to set file permissions in linux but I am a little confused.  Is it only possible to have 1 group per file/directory or can you have multiple groups and then give them different levels of access?  I have looked at the Permissions tab in Nautilus and at chmod from the command line and I don't see any way to have multiple groups.  Also, is there any way to recursively set the file permissions in Nautilus?

---

### Post by mority on 2006-08-07
> **Paul41 said:**
> I am trying to understand how to set file permissions in linux but I am a little confused.  Is it only possible to have 1 group per file/directory or can you have multiple groups and then give them different levels of access?  I have looked at the Permissions tab in Nautilus and at chmod from the command line and I don't see any way to have multiple groups.  Also, is there any way to recursively set the file permissions in Nautilus?

Every file (including directories) on a Unix system (including Linux) belongs to exactly one user and exactly one group.

I don't think it is possible to set file permissions recursively in nautilus but it's easy to do it with the chmod command and the -R option:```
chmod -R permissions directory
```

---

### Post by Paul41 on 2006-08-07
Thanks for the info.  That clears things up for me.

---

### Post by lamego on 2006-08-07
You can only assign a group/user as the file owner, on a terminal type "man chmod" and "man chown" it should more helpfull than nautilus help...

---

### Post by colo on 2006-08-07
That is, with traditional UNIX-style permissions. The Linux-kernel implements more complex ACLs (Access Control Lists) via an Extended Attributes (xattr) namespace for the most common filesystems.

---

