---
title: "su problem"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-02-16
I can sudo and gksudo just fine with my password, but if I want to do su I get an authentication failure. How can I fix this?

---

### Post by sardion on 2007-02-16
Better plan: (what I do when I really need to just be root):

sudo su -

will behave like su but by way of sudo.


If you really want to su ...
you need to create a password for root in order to su to root.

This is not recommended but if you *know* what you are doing then you can do so by

sudo passwd root

then enter a password for root.

---

### Post by syalam on 2007-02-16
good idea! it worked

---

### Post by ardchoille42 on 2007-02-16
The reason you couldn't use su is because su was expectiing root's password (this is different from the admin user's pass created during installation) and you don't know root's password. sudo su isn't a good idea either as it doesn't set up the environment properly. Better to use sudo -i in a terminal.

---

### Post by sventovit on 2008-07-19
You just have to put "sudo -s" and it opens root shell (shell type is defined by SHELL environment variable).

---

