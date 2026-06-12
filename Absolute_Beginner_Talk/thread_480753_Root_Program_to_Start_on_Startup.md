---
title: "Root Program to Start on Startup"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Majorix on 2007-06-21
I want a program that requires root password to start on startup. For example mysql. But when I set that under Preferences>Sessions nothing happens.

Any suggestions?

---

### Post by 5-HT on 2007-06-21
You can start it with root privs by invoking it  from /etc/rc.local

---

### Post by Majorix on 2007-06-21
I don't have any /etc/rc.local? Maybe that's because you are on a different distro...

---

### Post by 5-HT on 2007-06-21
You should have an /etc/rc.local on Ubuntu. Search your filesystem for rc.local to double check. You can create it if not. Otherwise, you can mess around with runlevels.
cheers,

---

