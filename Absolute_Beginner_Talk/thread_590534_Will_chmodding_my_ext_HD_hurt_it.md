---
title: "Will chmodding my ext HD hurt it?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Halfling Rogue on 2007-10-24
Right now my external hard drive has permissions set at:

```
lrwxrwxrwx  1 root          root              6 2007-07-23 18:01 cdrom -> cdrom0
drwxr-xr-x  2 root          root           4096 2007-07-23 18:01 cdrom0
lrwxrwxrwx  1 root          root              7 2007-07-23 18:01 floppy -> floppy0
drwxr-xr-x  2 root          root           4096 2007-07-23 18:01 floppy0
drwx------ 20 halflingrogue halflingrogue 32768 1969-12-31 16:00 LA HUEVOSA
```

I want to chmod it to 755 to see if that helps with some problems I've been having with it, but I'm not quite sure if setting chmod on it is safe.

---

### Post by reeseslover531 on 2007-10-24
that is fine.  It won't hurt the drive physically in any way.  Yes technically it allows more people to do stuff with that drive, but assuming that there is nothing super secret, you will be fine.

---

