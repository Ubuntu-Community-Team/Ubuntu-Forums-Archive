---
title: "How to delete XORG file?"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by EGE-FB on 2006-11-12
I am new to Ubuntu, and I struggled for 2 hours to fix my screen resolution issue. I wanted a 1280x800 resolution on my laptop and only managed to get this after installing the ATI drivers. Anyways, along the way, I managed to create 4 xorg.conf files that aren't in use now. How do I delete them? (They are useless). An example of one of the files is "xorg.conf.20061111214718". I don't have permission to delete them because I don't have root privileges.

Any help would be appreciated. Thanks

---

### Post by taurus on 2006-11-12
Open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo rm /etc/X11/xorg.conf.*
```

---

### Post by EGE-FB on 2006-11-12
Great, that did the trick, thanks a lot :)

---

