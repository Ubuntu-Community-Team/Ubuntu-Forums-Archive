---
title: "[SOLVED] Update Manager error"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Motorhead Kaze on 2007-07-22
Hi there.

I read other posts regarding Update Manager troubles, but they don't help fix my trouble.  The message I get is:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I did a Alt+F2 and ran the 'dpkg --configure -a' thing and nothing happened at all.  Was I supposed to run it somewhere else?

Appreciate the help.  (I'm using Feisty btw)

---

### Post by LuisAugusto on 2007-07-22
Press ALT + F2

```
gksu dpkg --configure -a
```

or in a gnome-terminal:

```
sudo dpkg --configure -a
```

I don't understand why Ubuntu don't tell people how commands are, newbies won't know they have to run it as a root.

Hope this help you

---

### Post by Motorhead Kaze on 2007-07-23
Ahhh.  Thank you.  That was exactly what I needed!

---

