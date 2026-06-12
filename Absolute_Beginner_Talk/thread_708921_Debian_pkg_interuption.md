---
title: "Debian pkg interuption"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by SILLAT on 2008-02-26
can any one help me with this: i was installing java 6 then it got interupted during the final installation an now everytime i try to install a software application i get  this message:
[COLOR="Red"]dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. [/COLOR]
how do i get around this
 i'm using ubuntu 7.10

---

### Post by taurus on 2008-02-26
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

p.s.  Make sure you close down whatever window you have open when you received that error message.

---

### Post by SILLAT on 2008-02-26
works like a charm
thanks man

---

