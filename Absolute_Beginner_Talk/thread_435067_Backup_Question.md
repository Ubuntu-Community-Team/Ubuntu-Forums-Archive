---
title: "Backup Question"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by bodam on 2007-05-06
After some problems, I am now able to use SimpleBackup to backup my system.  Something about it though, does not make sense to me.  The backups are stored in /var/backuo, which I do not have access to, so how can I copy them off for safekeeping?  I have an external USB drive where I would like to keep them, just in case.

What am I missing

---

### Post by starcraft.man on 2007-05-06
> **bodam said:**
> After some problems, I am now able to use SimpleBackup to backup my system.  Something about it though, does not make sense to me.  The backups are stored in /var/backuo, which I do not have access to, so how can I copy them off for safekeeping?  I have an external USB drive where I would like to keep them, just in case.

What am I missing

Simple fix, open the terminal and then type in...

```
gksudo nautilus
```

You should be able to access any folder and file after that.

---

### Post by Skrynesaver on 2007-05-06
Did you run sbcp ?(The simple backup configuration program)
You can specify the USB drive as the location to backup to here

---

