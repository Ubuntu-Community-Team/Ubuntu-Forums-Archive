---
title: "how to make desktop links"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by andhar on 2007-11-18
On windows machine you can map networked drives and then make iconed links on your desktop or in any other folder if you need to. 

How was I go about simply linking via Icons the network drives I need I've done it in KDE but I can't figure it out in Gnome.

Thanks In advanced.

---

### Post by odiseo77 on 2007-11-18
Hi, try this (in a console as a plain user):

```
cd Desktop
ln -s /path/to/your/network/drive
```

Greetings.

---

