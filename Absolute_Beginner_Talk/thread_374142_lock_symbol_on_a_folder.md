---
title: "lock symbol on a folder?"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by a_lacsa on 2007-03-02
hello..

I noticed that there is lock symbol on my apache2 folder. and if i try to explore it, it doesnt show anything.

what does it mean? how can I see the files inside a locked folder?

---

### Post by scxtt on 2007-03-02
the "lock" means you don't have "read" and/or "execute" access to the folder (i.e. there is no "read" access for "other" (or "group")) ... you'll have to see who owns the folder and what the permissions are ...

what specific "apache2" folder are you referring to?

---

### Post by a_lacsa on 2007-03-02
because im trying to find the location where the config file is.. i found that folder in /usr/var/lock.

funny though.. i installed apache2 using my account.. why is it locekd?

---

### Post by scxtt on 2007-03-02
the config for apache2 is in /etc/apache2/apache2.conf (you can use /etc/apache2/httpd.conf for somethings too)

mine are both owned by root ...

:> ll /etc/apache2/httpd.conf
-rw-r--r-- 1 root root 268 2006-08-18 20:09 /etc/apache2/httpd.conf

:> ll /etc/apache2/apache2.conf
-rw-r--r-- 1 root root 13K 2006-08-17 01:58 /etc/apache2/apache2.conf

you would have had to use sudo to install apache2 (or any program) - so "who" you installed it as is irrelevant ...

---

