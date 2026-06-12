---
title: "Debian packages freeze up computer"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by lord.toan on 2007-11-10
Any time I try to install a .deb package, it freezes up my entire computer and then I have to wait a minute til the program finally kills itself...

Any way I can fix this?

---

### Post by kerry_s on 2007-11-10
ubuntu is not debian. ubuntu is based on debian. alot no longer compatible.
how are you installing? synaptic, add remove, dpkg -i
what are you trying to install?

---

### Post by lord.toan on 2007-11-13
ANYTHING that's a .deb package, the debian installer program comes up, and when i click install, it just locks up and after a few minutes of lagging my entire computer to hell, it just disappears.

---

### Post by jw5801 on 2007-11-13
Try running it from the command line, so we can get some reasonable error messages:
```
sudo dpkg -i *packagename*.deb
```

---

