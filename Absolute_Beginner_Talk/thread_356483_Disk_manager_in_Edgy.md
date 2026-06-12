---
title: "Disk manager in Edgy?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by l0k1_ on 2007-02-08
I swear there was a tool in the administrative options that allowed me to see the partitions and free space left on my disk ... right now there isn't. Was I just seeing things / did it disappear / is it called something else?

---

### Post by benuski on 2007-02-08
Maybe you're thinking of the disk usage manager?  Its under programs->accessories, I believe.  Or maybe you're thinking of GParted, which is on the liveCD but not on the real installation by default.

---

### Post by etank on 2007-02-08
The non-gui way to do it would be to drop into a terminal and enter```
df -h
```That will give you the disk free in human readable format on all partitions that are mounted.

---

### Post by kebes on 2007-02-08
In Dapper there was a util called "disks-admin" that would show you partitions. Apparently it's been retired or something because it's not in Edgy and I can't even find it in the Dapper repositories anymore (though it's still installed on one of my machines running Dapper). Here's another thread complaining about this:
[http://www.ubuntuforums.org/showthread.php?t=285279](http://www.ubuntuforums.org/showthread.php?t=285279)

The only substitute I'm aware of is using "gparted", or the commandline "df" and "fdisk -l".

---

