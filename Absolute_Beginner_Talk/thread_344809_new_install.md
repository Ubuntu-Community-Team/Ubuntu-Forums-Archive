---
title: "new install"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Vanha on 2007-01-23
I just installed ubuntu 6.10 for the first time. during the install it asked for user ID and password. once the system restarts i can log in as the user, but i have no idea what the root password is. it never asked me for one. is this normal or did i miss something?

---

### Post by bulldog on 2007-01-23
You have no root password.
You can use sudo if you need root permissions,or if you need to be root for a longer period use sudo -s.

---

### Post by steve.horsley on 2007-01-23
To expand on Bulldog's reply:

You cannot log in as root - the account is disabled. If you wantto do things outside your home folder, e.g. sysadmin tasks, you can tell the computer to run tasks with root privilege without logging in as root. You do this by preceeding the command you want run with sudo (think Super User Do). Frexample, editing /etc/fstab is not allowed to normal users (it's read only), but you can do it with this command:
**sudo nano /etc/fstab**

If you want to launch graphical programs, use gksu instead (complicated reasons):
**gksu gedit /etc/fstab**

A very useful one to remember is **gksu nautilus**, but remember you can now trash the entire system. And as Bulldog says, if you expect to do a lot of commands, use **sudo su** or **sudo -s** to get a command prompt with root rights. 

No need to log out and in again. Easy.
Also see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Vanha on 2007-01-24
thanks for the help

---

