---
title: "su [Resolved]"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by raharris on 2007-01-09
HI -- I've opened the terminal and am trying to log in as a superuser.  I just set up Ubuntu today and when I did I entered a username and password.  Those credentials are good enough to log me into my Ubuntu iteration, but I assumed I could use the same credentials to become the superuser.  Not the case?  If not, how do I create a superuser?  Can't install most software without that admin level.
thanks, RA Harris

---

### Post by meng on 2007-01-09
The root user can be enabled, but the conventional way to do root-y things in ubuntu is to preface each command with sudo
e.g.
sudo make install

But I think you can (if you must) enable the root account by
sudo su

---

### Post by aysiu on 2007-01-09
Read this:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by obsidion on 2007-01-09
> **meng said:**
> The root user can be enabled, but the conventional way to do root-y things in ubuntu is to preface each command with sudo
e.g.
sudo make install

But I think you can (if you must) enable the root account by
sudo su


  Sort of it makes you superuser until you close that terminal without having to retype the password every 15minutes. You can enable the root account but it will cause some apps to become confused in the gui as to which password is needed. So on the whole it is better/easier not to.

visit here for more information

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by raharris on 2007-01-09
Right guys -- thanks for the help!

RAH

---

