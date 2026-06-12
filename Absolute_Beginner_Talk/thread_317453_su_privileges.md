---
title: "su privileges"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by cacharreo on 2006-12-12
Hi people.
How I do to configure an aplication launcher so the system tell me about the su password automacally when launch this one?
untill the momment I do it from the terminal:
*sudo xxxxxxx * but sometimes is uncomfortable for me.

Thank you all :-D

---

### Post by tkjacobsen on 2006-12-12
right-click on the launcher -> properties. Then insert "gksudo" in front of the command (without the quotes).

---

### Post by aysiu on 2006-12-12
Use *gksudo* instead of *sudo*.

For example, if you want to launch Nautilus as root, make the launcher command: ```
gksudo nautilus
```

---

