---
title: "Internet Security in Ubuntu"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by quincyjones on 2006-04-23
Hi,
I understand that I don't need an antivirus, anti-spyware, is that right? What about a firewall?

Thanks :rolleyes:

---

### Post by xXx 0wn3d xXx on 2006-04-23
[QUOTE=quincyjones]Hi,
I understand that I don't need an antivirus, anti-spyware, is that right? What about a firewall?

Thanks :rolleyes:[/QUOTE]
Ubuntu has a built in firewall. It's called iptables. If you would like a gui to control iptables, install firestarter. To get firestarter, type the following in terminal.

> sudo apt-get firestarter

Then follow [ this guide ](http://ubuntuforums.org/showthread.php?t=110320&highlight=firestarter+startup+password) to make firestarter load on startup.

---

### Post by derjames on 2006-04-23
Hi there
This wiki may be useful to learn the basics of iptables and install any antivirus (if needed...)

[https://wiki.ubuntu.com/Security](https://wiki.ubuntu.com/Security)

cheers

---

### Post by steve.horsley on 2006-04-23
A default Ubuntu install doesn't need a firewall because it's not running any services that listen for incoming connections. If you install and start your own services, like file sharing, you may want to add a firewall to control who accesses those services.

---

