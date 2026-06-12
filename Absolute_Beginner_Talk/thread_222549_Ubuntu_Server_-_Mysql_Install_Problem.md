---
title: "Ubuntu Server - Mysql Install Problem"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Nalum on 2006-07-25
Hello i've just installed ubuntu server on my old pc and have been following this set up guide [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)
i'm now on page 4 and am trying to install mysql this is the message i get when i type in the command used on the tutorial

> root@testserver: apt-get install mysql-server mysql-client libmysqlclient12-dev
Reading package lists... Done
Building dependency tree... Done
Package libmysqlclient12-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libmysqlclient12-dev has no installation candidate

anyhelp greatly appreciated.

Thank you
Nalum

---

### Post by sebz2005 on 2006-07-25
Just go
```
sudo -s
Password:
apt-get install mysql-server
```
That should install the client.

---

### Post by Nalum on 2006-07-25
> **sebz2005 said:**
> Just go
```
sudo -s
Password:
apt-get install mysql-server
``` That should install the client.

Thanks sebz thats worked

---

### Post by sebz2005 on 2006-07-25
You're welcome. I've recently done that myself and search 2 hours just to find that!

---

