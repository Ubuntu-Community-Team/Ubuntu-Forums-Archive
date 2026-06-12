---
title: "Error on Add/Remove applications"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-08-28
I got an error when I try to install something from Add/remove applications:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried downloading Ubuntu supported thing but the same error...what could it be?

---

### Post by mcduck on 2007-08-28
Open a terminal and try running "sudo dpkg --configure -a" like the error message suggests. That should fix the problem. :)

---

### Post by Fixman on 2007-08-28
Well, thaniks a lot. I have tried that, but without the sudo thing at the beginning. What does exacly sudo do? execute a program like a superuser?

---

### Post by Seisen on 2007-08-28
Basically in a nutshell yes that is exactly what it does.

---

### Post by por100pre1 on 2007-08-28
> **Fixman said:**
> Well, thaniks a lot. I have tried that, but without the sudo thing at the beginning. What does exacly sudo do? execute a program like a superuser?

Exactly. Execute a program like a superuser. :)

---

### Post by Fixman on 2007-08-28
Using the command line for executing a program as a superuser? 3 days before this, when I still used windows, couldn't even imagine it. This OS owns!

---

### Post by mcduck on 2007-08-28
> **Fixman said:**
> Well, thaniks a lot. I have tried that, but without the sudo thing at the beginning. What does exacly sudo do? execute a program like a superuser?

'sudo' alone executes program as superuser, just like you said. But it can also be used to run command as any other user.  (sudo -u username command)

For graphical programs use 'gksudo' instead of sudo, it loads root user's profile correctly (avoiding some problems that can result from starting GUI applications with 'sudo') and also provides you with a popup asking for your password so you can use it when you create menu entries or desktop/panel launchers.

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

edit: too slow :D

---

