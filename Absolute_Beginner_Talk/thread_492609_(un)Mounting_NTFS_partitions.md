---
title: "(un)Mounting NTFS partitions"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by lbelloq on 2007-07-04
Hello all.

My computer is dual-booting XP and Ubuntu. I have 2 hard disks, one for operating system and other for documents and settings. Both are NTFS or ext2 where applicable.
When I'm using Ubuntu, I can see the NTFS partitions in File Browser, but when double-clicking to mount them, an error appears:
org.freedesktop.Hal.Device.PermissionDeniedByPolicy
If I add, from my user account, umask=0222 to the mounting options, it works only in my account, and if I try from other account, it doesn't work.
What I want to do is that all users be able to (un)mount those partitions at will. Maybe I can set global options for that; how can I do it?

---

### Post by dreadlord_chris on 2007-07-04
> **lbelloq said:**
> Hello all.

My computer is dual-booting XP and Ubuntu. I have 2 hard disks, one for operating system and other for documents and settings. Both are NTFS or ext2 where applicable.
When I'm using Ubuntu, I can see the NTFS partitions in File Browser, but when double-clicking to mount them, an error appears:
org.freedesktop.Hal.Device.PermissionDeniedByPolicy
If I add, from my user account, umask=0222 to the mounting options, it works only in my account, and if I try from other account, it doesn't work.
What I want to do is that all users be able to (un)mount those partitions at will. Maybe I can set global options for that; how can I do it?

You should be be able to add the **user** option to the mount line for that partition in /etc/fstab - no need to muck about with permissions:
i.e.
```

# /dev/hdd1 - DriveB NTFS data
UUID=45eb76ed-6043-41ab-a272-6776dd6f1713 /media/DriveB ntfs **user**,noauto 2 0

```

---

### Post by lbelloq on 2007-07-04
All right.
Now, what's that UUID line and how can I obtain that info? cause I don't think it will be the same for my system.

---

### Post by bradmayne on 2007-07-04
search for my how to view windows files!!  I have it there step by step!!

---

### Post by dreadlord_chris on 2007-07-05
> **lbelloq said:**
> All right.
Now, what's that UUID line and how can I obtain that info? cause I don't think it will be the same for my system.

```

ls -l /dev/disk/by-uuid/

```

---

### Post by lbelloq on 2007-07-05
> **dreadlord_chris said:**
> ```

ls -l /dev/disk/by-uuid/

```

> **bradmayne said:**
> search for my how to view windows files!!  I have it there step by step!!
Many thanks. I'll try it when I get home.

EDIT: I'll try another approach. Many thanks for your help.

---

