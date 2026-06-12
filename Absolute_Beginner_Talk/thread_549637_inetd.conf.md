---
title: "inetd.conf"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by joot211 on 2007-09-12
I remember adjusting inetd.conf in the past to controll daemons. I took a look at mine on fiesty just to see what services are running ( aside from a port scan) and I saw only one entry in the whole file;

vboxd   stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/vboxd

anyone know what this daemon is all about and is the daemons still controlled by making adjustments to etc/inetd.conf like before. I sue it&#347; easy to apt-install the required like ssh, but I want to get into the guts of it, so any info would be appreciated.

---

### Post by Harpoon on 2007-09-12
I am not sure exactly what you are asking, but vboxd is a daemon associated with the voice box program.

---

