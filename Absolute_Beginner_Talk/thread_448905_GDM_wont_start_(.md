---
title: "GDM wont start :("
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Bright Hammer on 2007-05-19
Hi I need some help. I enabled xdmcp and now when i boot all i get is a black screen and an hourglass. I cant log in to disable it. I am currently in the recovery mode trying fix the problem. Can someone help me disable xdmcp manually?

---

### Post by yabbadabbadont on 2007-05-19
Remove or rename /etc/gdm/gdm.conf-custom then run /etc/init.d/gdm restart

---

### Post by Bright Hammer on 2007-05-19
Thanks that fixed the problem.:)

---

