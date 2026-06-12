---
title: "dpkg --remove command"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Hotchilli on 2006-01-15
trying to remove webmin and also kerio mail server
but how do I know the files they come in?



thanks

hc
:smile: 
andy108@heis:~$ sudo dpkg --remove webmin_1.250-2_all.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

---

### Post by bags on 2006-01-15
try sudo apt-get remove webadmin and so on...

---

### Post by Arktis on 2006-01-15
Why not just use synaptic package manager?  It's nifty, it's a GUI for apt-get, it's got a search feature, and it wants to be your buddy.  System > Administration > Synaptic Package Manager

---

### Post by Hotchilli on 2006-01-15
thanks but sysnapic out of action
see
[http://www.ubuntuforums.org/showthread.php?t=108603](http://www.ubuntuforums.org/showthread.php?t=108603)

thanks

hc:smile:

---

