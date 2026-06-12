---
title: "samba security"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-28
now how do i make my samba connections more secure?  perhaps passwords?  do i even need it if i have my firewall on and a router?

---

### Post by dmizer on 2006-05-29
secure passwords are fundamental.

configure your firewall so it can share with the local network but not with the wide area network (internet) side.

how you configure your entier network can be helpfull too.  isolate it from the internet connection and don't give it permission to access the outside.  just have it serve up files. (ie. dedicate a box for your shares).

---

