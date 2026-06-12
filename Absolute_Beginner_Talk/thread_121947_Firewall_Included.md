---
title: "Firewall Included?"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by Animortis on 2006-01-26
After digging through the system settings, I've yet been able to determine if there's a firewall included in Ubuntu.

So, is there one? And if so, what's the best means to configure it?

---

### Post by ubuntuuser on 2006-01-26
Yes. there is one. It is called iptables. A nice frontend for iptables is firestarter. To get firestarter, type ```
sudo apt-get install firestarter
```. Or type ```
man iptables
``` at the command line to learn more about iptable's syntax.

---

### Post by qwazert on 2006-01-26
It "should be" included during the install, it's called IPTables.
The easiset way to configure is by using a program called Firestarter, available in the Synaptic Packages.

Or you could run EasyUbuntu, which does it for you but be warned...it takes a while!


Doh! Duplicate Post.....

---

### Post by nesman89 on 2006-01-26
try firestarter.  [http://www.fs-security.com/](http://www.fs-security.com/)

or you could try Automatix it install lot's of good software to get your new install up and running.  do a search in the forums

---

