---
title: "Installed kubuntu instead of ubuntu!?*"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by stpike on 2007-04-26
Hi,

I have a new laptop, 80GB and wanted to install a dual boot Ubuntu/XP Pro system 40GB each.  I installed Kubuntu by mistake.  How can I remove Kubuntu and install Ubuntu in its place?

thanks

---

### Post by aysiu on 2007-04-26
Do this:
[http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)

and then this:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Seisen on 2007-04-26
All you need to do is run the Ubuntu install disc instead of the Kubuntu install disc and do exactly what you did before.

---

### Post by stpike on 2007-04-27
Aysiu,

I tried to follow your suggestion but I am not root.  How do I find the default root password for new installations to complete the download of gnome?

---

### Post by aysiu on 2007-04-27
You don't have to be root. *sudo* allows you to temporarily assume root privileges. So instead of doing (you need root--other Linuxes) ```
**su**
password:
[b]aptitude update
aptitude install ubuntu-desktop[/b]
``` you do this (you don't need root--Ubuntu/Kubuntu): ```
**sudo aptitude update**
password:
**sudo aptitude install ubuntu-desktop**
``` If you get any errors, post back everything from the terminal (highlight everything--both what you typed *and* what errors you got--then copy and paste).

---

