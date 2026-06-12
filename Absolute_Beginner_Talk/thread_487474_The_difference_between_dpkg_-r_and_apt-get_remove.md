---
title: "The difference between dpkg -r and apt-get remove"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by mocqueanh on 2007-06-29
these 2 commands is uninstall program in Ubuntu, but i dont know the difference of them, Do you know ?

---

### Post by waylandbill on 2007-06-29
apt-get (as well as deslect and aptitude) is a front end to dpkg. One could do everything directly via dpkg, but these applications add more feature such as being able to remove packages automatically installed as a dependency.

---

### Post by mocqueanh on 2007-06-30
So, dpkg -r dont remove dependencies of software when i uninstall it ?

---

