---
title: "Blocking ports"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by kmifflin on 2006-01-10
Hello again.  Well I'm a Linux nooobie.  Fortunately I come from a background of having to use DOS a lot so I'm getting used to typing commands at the terminal and installing applications and editing config files.

I ran Nessus and it says I have a port open that I really need to close.

How do you close ports or at least disable them

Thanks, btw Ubuntu rocks.  I had no problems installing it and the only major issue that I had (that I discovered so far) was with the DNS server entries in resolv.conf

Any help would be appreciated.  Thanks

---

### Post by paulmilliken on 2006-01-10
To close a port, you need a firewall.  I believe Ubuntu doesn't have a firewall installed by default because there are no applications that listen to any of the ports enabled by default.  A firewall can either be installed on a router (if you have one) or on your desktop computer.  There are several firewalls available in the repositories if you decide that you want one.

Furthermore, most firewalls have all ports closed by default so you will probably have to open all but the one that you want to close.

Paul

---

### Post by Sef on 2006-01-11
To install a firewall, do this:  Applications --------> Add Applications -------> Password ------> System Tools -------> more programs  --------> click on Firestarter.  (If it gives you a notice about a respository needing to be open, click yes/ok. [I forgot what it says exactly.])

---

### Post by byen on 2006-01-11
yes..or you can also...Applications>Accessories>Terminal
code: sudo apt-get install firestarter

Hope that helps...goodluck and welcome to Ubuntu.

---

### Post by cwaldbieser on 2006-01-11
[QUOTE=paulmilliken]To close a port, you need a firewall.  I believe Ubuntu doesn't have a firewall installed by default because there are no applications that listen to any of the ports enabled by default.  A firewall can either be installed on a router (if you have one) or on your desktop computer.  There are several firewalls available in the repositories if you decide that you want one.

Furthermore, most firewalls have all ports closed by default so you will probably have to open all but the one that you want to close.

Paul[/QUOTE]
In most major Linux distros, the firewall (Netfilter) is compiled into the kernel, and Ubuntu is no exception.  There is even a CLI front end called "iptables" which is included.

Firestarter is a nice graphical front-end, though.

---

