---
title: "How to uninstall as root"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-11-09
I am currently trying to uninstall CrossOver and it tells me to fully uninstall it I need to run /opt/cxoffic/bin/cxuninstall as root.
How do I go about doing that

---

### Post by Iceni on 2007-11-09
either gksu nautilus and click it

or use sudo before your command in terminal.

---

### Post by Dr Small on 2007-11-09
Edit.
Oops. I missed part of his statement.

Yeah, run:
```
sudo /opt/cxoffic/bin/cxuninstall
```

---

### Post by Iceni on 2007-11-09
Allow me to explain really quickly:

In ubuntu you are not by default administrator. This is for security reasons and so you won't delete something stupid that will break your system. To enter administrator mode you use "sudo" (for command line) or "gksu" (for graphical interface) to temporarily run programs with administrator rights.

---

### Post by Dr Small on 2007-11-09
> **Iceni said:**
> Allow me to explain really quickly:

In ubuntu you are not by default administrator. This is for security reasons and so you won't delete something stupid that will break your system. To enter administrator mode you use "sudo" (for command line) or "gksu" (for graphical interface) to temporarily run programs with administrator rights.
More information here, also:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

