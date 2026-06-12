---
title: "Ext3 partition not writable"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by punong_bisyonaryo on 2007-05-06
Good day to all!

I have installed Ubuntu several times before, and for ext3 partitions, it automatically permits me to read/write automatically. No set up needed.

However on one machine, I can't write to my ext3 partition. I know I need to edit fstab and do something, but I think I've forgotten. I've tried adding gid and such, but it won't work. I must've forgotten something. Please help.

```
/dev/hda7   /media/hda7   ext3   defaults,charset=utf8,gid=047,uid=47,umask=222
```

---

### Post by Bachstelze on 2007-05-06
Stick with just *defaults* as mount parameters and use chown/chmod to tweak permissions to your needs. uid/gid/umask are used on NTFS or FAT partitions sich you can't use chow/chmod on them.

---

