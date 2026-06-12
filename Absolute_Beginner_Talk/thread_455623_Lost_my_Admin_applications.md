---
title: "Lost my Admin applications"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Ephilei on 2007-05-26
The usual list of apps in System/Admin/ is missing, except for a few like System Monitor. What gives?

The last thing I did was logout because the process gij (a java daemon) wasn't responding.

---

### Post by oilchangeguy on 2007-05-26
> **Ephilei said:**
> The usual list of apps in System/Admin/ is missing, except for a few like System Monitor. What gives?

The last thing I did was logout because the process gij (a java daemon) wasn't responding.

how did you log out?

---

### Post by Dzenhax on 2007-05-26
Try right clicking on applications and then choose edit menus.  You should be able to bring them back from there.

---

### Post by Ephilei on 2007-05-26
Okay, the problem is that my user has been taken off the sudoers file. How do I get back on? I don't have read or write access to sudoers and I'm the only user on this system. I disabled root login from the local machine and ssh.

---

### Post by Nikron on 2007-05-26
> **Ephilei said:**
> Okay, the problem is that my user has been taken off the sudoers file. How do I get back on? I don't have read or write access to sudoers and I'm the only user on this system. I disabled root login from the local machine and ssh.

You boot into the machine in single user mode.

---

### Post by Ephilei on 2007-05-26
Ok, that did it! Thanks

---

