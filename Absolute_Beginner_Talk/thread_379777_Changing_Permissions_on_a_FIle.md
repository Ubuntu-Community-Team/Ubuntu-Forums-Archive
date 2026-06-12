---
title: "Changing Permissions on a FIle?"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Sleestack on 2007-03-08
I want to enable the universe and multiverse repositories in my sources.list but when I try to save the file in gedit it won't let me save it. The file browser tells me I'm not the owner and can't change the permissions. I guess I need to do this from the terminal. What are the commands?

---

### Post by taurus on 2007-03-08
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by aysiu on 2007-03-08
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

