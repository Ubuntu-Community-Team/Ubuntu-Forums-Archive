---
title: "Sessions"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by qwazert on 2007-12-17
Is there a way to edit the SESSIONS list?
I hate XFCE (doesn't load properly) so I would like to remove it as an option from the list!

Thank you in advance...

---

### Post by yabbadabbadont on 2007-12-17
There should be a file in /usr/share/xsessions that is called something like "xfce.desktop".  You need to remove that file.  I would just move it in case you ever want it back again.  In a terminal window run:
```
sudo mv /usr/share/xsessions/xfce.desktop /root
```
That will move the file to root's home directory.  You could restore it later by running:
```
sudo mv /root/xfce.desktop /usr/share/xsessions
```

---

