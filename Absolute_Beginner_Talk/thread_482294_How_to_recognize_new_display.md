---
title: "How to recognize new display?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by lift_test on 2007-06-23
I've got a new display that is 3:1 and (I'm fairly sure) is higher resolution than the original CRT.  How do I get Ubuntu to change to the new resolution?

---

### Post by taurus on 2007-06-23
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by lift_test on 2007-06-23
Sorry to be dense but that gives me a dialogue that is asking about the graphics card not the display, if I have to go through this first how do I find out what the onboard graphics "card" is?
Thanks for the help so far
Vic

---

### Post by taurus on 2007-06-23
```
lspci | grep VGA
```

---

