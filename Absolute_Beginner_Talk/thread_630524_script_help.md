---
title: "script help"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by billt31 on 2007-12-03
what is this and how do i run it and its an error "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." its thrown up whenever i use an administrative application

---

### Post by bwald on 2007-12-03
This means you were running the Package Manager, or Synaptic or something and it crashed or you turned off your computer.  To fix it run:

```
sudo dpkg --configure -a
```

in a terminal.  dpkg is a program used by Ubuntu to configure packages that you've installed.

---

