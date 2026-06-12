---
title: "Dpkg config????"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by nynoah on 2007-07-25
I am having problems with my updates...........does anyone know what is going on?

Noah




noah@noah-desktop:~$ sudo dpkg --configure -a
Password:
Setting up phpgroupware (0.9.16.011-3) ...
setting up apache
setting up apache-ssl
setting up apache-perl
setting up apache2
/usr/share/wwwconfig-common/pgsql.get: line 77: psql: command not found
/usr/share/wwwconfig-common/pgsql.get: line 77: psql: command not found
dpkg: error processing phpgroupware (--configure):
 subprocess post-installation script returned error exit status 1
Setting up lftp (3.5.11-1~feisty1) ...

dpkg: dependency problems prevent configuration of phpgroupware-dj:
 phpgroupware-dj depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-dj (--configure):
 dependency problems - leaving unconfigured
Setting up libisc11 (9.3.4-2ubuntu2.1) ...

Setting up libdecoration0 (0.5.1+git20070719~jbs1) ...

Setting up liblwres9 (9.3.4-2ubuntu2.1) ...

---

### Post by jcarlock on 2007-07-25
Any particular reason you cannot use apt-get, or the synaptic package manager?

JC

---

