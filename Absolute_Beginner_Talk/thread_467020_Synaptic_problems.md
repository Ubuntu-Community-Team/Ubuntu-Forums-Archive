---
title: "Synaptic problems"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-06-07
Hi, when i try to start synaptic i get this [PHP]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

[/PHP] :(

Anny one?

---

### Post by taurus on 2007-06-07
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
```

---

### Post by ajmannen on 2007-06-07
Now it says that a packege is broken, and that i should use the filter, but when i try it finds no broken files...

---

### Post by taurus on 2007-06-07
It would be nice if you can post the whole error message when you run those two commands. from a terminal.

---

