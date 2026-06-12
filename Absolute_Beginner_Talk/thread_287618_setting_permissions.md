---
title: "setting permissions"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Meysys on 2006-10-29
I just installed ubuntu onto my laptop, everything is working great, however I need to know how to give myself permission to edit files in my computer

Specificly, I need to figure out how to edit the xorg.config file so that I can fix my screen resolution D:

---

### Post by taurus on 2006-10-29
Open a terminal, Applications -> Accessories -> Terminal, and type

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak <-- make a backup just in case...
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by aysiu on 2006-10-29
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

