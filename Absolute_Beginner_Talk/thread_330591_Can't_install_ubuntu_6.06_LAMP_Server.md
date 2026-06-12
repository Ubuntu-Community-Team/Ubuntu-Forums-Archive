---
title: "Can't install ubuntu 6.06 LAMP Server"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by iulian on 2007-01-03
Hello,
I have a live CD of Ubuntu 6.06. The problem is that after I boot from live cd and try to install Ubuntu with double click on the install icon from desktop I have no option of what I want to install: LAMP server, etc. Why?

---

### Post by az on 2007-01-03
> **iulian said:**
> Hello,
I have a live CD of Ubuntu 6.06. The problem is that after I boot from live cd and try to install Ubuntu with double click on the install icon from desktop I have no option of what I want to install: LAMP server, etc. Why?

Because the live cd is only for desktop installations.  You can, of course, install the LAMP stack on top of a desktop system if you want to.

To install just the server system, use the server install cd and pick the LAMP option.  Or the alternate cd and install a base system.  After that, install the LAMP stack

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by iulian on 2007-01-03
Thanks, I see your post very useful. I think I'll just install it using apt-get if nothing differs from the server system.

---

