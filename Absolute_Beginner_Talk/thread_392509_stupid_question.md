---
title: "stupid question"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by viergeame on 2007-03-24
I need to edit my xorg.conf, but i forget how to access it.  I have done it before, i just can't remember the command.  I know how to do everything once I get there.

---

### Post by invalid on 2007-03-24
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by ZeroWing on 2007-03-24
Nevermind. :)

---

### Post by viergeame on 2007-03-24
Thanks so much.  For some reason I was thinking it was just sudo and not gksudo.

---

### Post by invalid on 2007-03-24
> **viergeame said:**
> Thanks so much.  For some reason I was thinking it was just sudo and not gksudo.

Using sudo would also work, but it is not recommended for graphical applications. Graphical applications which require root privileges are safer when started using gksudo.

---

