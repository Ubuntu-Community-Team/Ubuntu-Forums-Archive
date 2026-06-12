---
title: "T or F:  diff -- root terminal vs. terminal + sudo"
date: 2005-05-18
forum: Absolute Beginner Talk
---

### Post by snairofilac on 2005-05-18
True or False:

There is a difference between using a root terminal and using a normal terminal and the sudo command.

thanks

---

### Post by az on 2005-05-18
Yes there is a difference.

When you run as root, you are the root user.  When you run as sudo, you are your user but have root priviledges.  Starting a program as root uses the settings in the root's home directory.  (/root)  Starting a program as your user using sudio uses your home director (/home/myself)

There are other obvious differences.  You need to type sudo before the command you want to run as root, for example, where when you runas root, you do not need to type sudo...

---

### Post by SNo0py on 2005-05-18
[QUOTE=azz]Starting a program as root uses the settings in the root's home directory.  (/root)  Starting a program as your user using sudio uses your home director (/home/myself)
[/QUOTE]Really? Did not know that - but good to know... Thanks for that tip!

---

### Post by snairofilac on 2005-05-19
azz you offer such excellent explanation  thanks for all your help

---

