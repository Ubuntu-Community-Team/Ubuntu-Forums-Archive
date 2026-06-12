---
title: "after install, gnome problem"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by ubum on 2008-03-10
My gnome window overlapped into many layers of gnome.  I can't use it.  How can I fix this problem?

---

### Post by jken146 on 2008-03-11
What do you mean?  GNOME is a desktop environment.  [http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)

Can you rephrase your question?

---

### Post by ubum on 2008-03-11
I can't access the gnome and login to the system.  It's is messed up.  How do I fix this.  Think either video card driver problem.

---

### Post by jan quark on 2008-03-11
what is your graphic card?

can you login into the failsafe gnome session?

perhaps you have to reconfigure the xserver, boot into the recovery mode and run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

