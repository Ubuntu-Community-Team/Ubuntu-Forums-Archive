---
title: "Bug? Signal 6 Sigabrt"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by suomalainen on 2007-12-12
Hej!

I wanted to ask the following. I'm running K3B and it crashes with the error stating to the effect Signal 6 SIGABRT.

Has anyone had this problem as well? It occurs during the copying process.

How would I go about repairing this?

Thank you.

---

### Post by mkoyle on 2008-01-16
From what you have posted, I can't figure out the problem.  

[http://bbs.archlinux.org/viewtopic.php?pid=108379](http://bbs.archlinux.org/viewtopic.php?pid=108379) has one guess... if you have the same problem, then opening a terminal (Applications --> Accessories --> Terminal) and typing

```
sudo /etc/rc.d/dbus start 
k3b
```

could make it work.

post the terminal output when you start k3b.

--Matthew

---

