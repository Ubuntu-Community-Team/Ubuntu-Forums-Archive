---
title: "installation issues"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by h4450 on 2007-12-12
I was trying to open up Hylafax on my Gibbon 7.10 server, but  I get this message.
E: Type 'sudo' is not known on line 58 in source list /etc/apt/sources.list

---

### Post by philinux on 2007-12-12
you need to 

gksudo gedit  /etc/apt/sources.list

Turn on line numbering in prefs and have a look at line 58.

---

### Post by aysiu on 2007-12-12
Or just [get a fresh sources.list](http://www.psychocats.net/ubuntu/sources#key).

---

