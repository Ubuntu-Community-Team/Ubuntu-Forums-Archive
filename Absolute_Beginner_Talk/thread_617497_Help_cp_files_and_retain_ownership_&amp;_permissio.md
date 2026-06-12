---
title: "Help: cp files and retain ownership &amp; permission"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by aspen_dv on 2007-11-19
I installed a 2nd hard disk to make more space for /home.  What I did was mount the new disk at /data and copied everything from /home to data, then make a symlink /home which point to /data
Everything seems to be ok, my users are able to log in, but they can't do anything at all due to permission issue. 
Apparently when I copy things from /home to /data as root, everything now owned by root. Is there a way to copy but retain the same ownership and permission? Thanks

---

### Post by bhold on 2007-11-19
Use the -p option. In a terminal window, type

```
man cp
```

for more information.

---

