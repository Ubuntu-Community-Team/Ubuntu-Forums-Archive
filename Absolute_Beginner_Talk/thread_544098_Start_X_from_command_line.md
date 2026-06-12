---
title: "Start X from command line"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by pgar23 on 2007-09-05
How do you start X form the command line?

---

### Post by aidanr on 2007-09-05
startx surprisingly enough, or better
sudo /etc/init.d/gdm start

---

### Post by mevets on 2007-12-04
thank you for answering this thread, it helped me out!

---

### Post by Dr Small on 2007-12-04
You can do it multiple ways, startx is just one of them.
You can also do:
```
xinit -- :1 vt12
```
To start a X display on Virtual Terminal 12, too.

---

