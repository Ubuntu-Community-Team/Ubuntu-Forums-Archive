---
title: "Root password"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Stephenkiley on 2007-12-12
I have installed Ubuntu 7.1.0 without a problem but I am unable to create a root password.  I have created users also.
Any suggestions?

---

### Post by g2g591 on 2007-12-12
you don't need a root password. Ubuntu is set up to use sudo, the first user created during install can use sudo command to run commands as root, for graphical apps use gksu (if using gnome) or kdesu (if using kde). Other users can use sudo if they are members of the admin group. you can get a root terminal by running sudo -i. If after reading all this you really think you need a root password, use sudo passwd root.

---

### Post by aysiu on 2007-12-12
You don't need a root password.

Why don't you explain what you're trying to do? Then we can explain how you're supposed to do it (without logging in as root).

---

