---
title: "unknown error"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by wsetchell on 2008-03-15
So I'm working on making a my own website using Ubuntu and Apache.  I'm following the instructions located here.  [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

The instructions have me copy and paste the default site to start my new one.  They say to use the command.

sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mysite 

This is what I get when I enter the command.

desktop:~$ sudo cp /etc/apache2/site-available/default /etc/apache2/site-available/mysite
cp: cannot stat `/etc/apache2/site-available/default': No such file or directory
will@tim-desktop:~$ 


Whats going wrong?

---

### Post by Oldsoldier2003 on 2008-03-15
> **wsetchell said:**
> So I'm working on making a my own website using Ubuntu and Apache.  I'm following the instructions located here.  [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

The instructions have me copy and paste the default site to start my new one.  They say to use the command.

sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mysite 

This is what I get when I enter the command.

desktop:~$ sudo cp /etc/apache2/site-available/default /etc/apache2/site-available/mysite
cp: cannot stat `/etc/apache2/site-available/default': No such file or directory
will@tim-desktop:~$ 


Whats going wrong?

typo. sites-available, not site-available

---

### Post by talsemgeest on 2008-03-15
Yeah, it always gives you that error when you are trying to work with a file or directory that doesn't actually exist.

---

