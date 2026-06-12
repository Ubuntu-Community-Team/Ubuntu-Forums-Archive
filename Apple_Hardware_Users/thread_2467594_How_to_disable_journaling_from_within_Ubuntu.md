---
title: "How to disable journaling from within Ubuntu"
date: 2021-10-01
forum: Apple Hardware Users
---

### Post by oidicle on 2021-10-01
Good day

I've been following this thread [http://ubuntuforums.org/showthread.php?t=1420673](http://ubuntuforums.org/showthread.php?t=1420673) regarding disabling journaling on an HFS+ HDD from within ubuntu. It turns out there's a code I need to compile from [https://pastebin.com/W8pfgHRe](https://pastebin.com/W8pfgHRe) in ubuntu to disable it.

How can I go about compiling it. I'm a newbie linux user willing to learn.

Please assist. Thanks

---

### Post by TheFu on 2021-10-01
Wouldn't mounting the file system as read-only disable journaling?
For read-write mounts, journaling is a good thing. I think that is accepted.

---

