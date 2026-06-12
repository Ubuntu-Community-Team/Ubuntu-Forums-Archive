---
title: "Using Cron"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by TannerLD on 2006-09-07
Hi all,

I'd like to put an entry in crontab, but I can't use nano because it isn't working for me and gedit won't save. Am I missing something?

Thanks
-Tanner

---

### Post by whizbaby on 2006-09-07
Not talkin much, huh? Me too;) 
[http://doc.gwos.org/index.php/Crontab](http://doc.gwos.org/index.php/Crontab)

---

### Post by Iowan on 2006-09-07
**Nano** isn't working... in what way?
Have you tried **gksudo gedit**?

---

### Post by TannerLD on 2006-09-07
> **Iowan said:**
> **Nano** isn't working... in what way?
Have you tried **gksudo gedit**?

It won't close. ^X isn't closing it.

I've used 'EDITOR="gedit" crontab -e' to open it in gedit.

-Tanner

---

### Post by Linux Lover on 2006-09-09
I am writing this :

$ sudo gedit /etc/cron.hourly/mytest

also changed the permission by sudo chmod 777 to that file.

edited the file as like:
=============================================
#!/bin/sh
#

04 * * * * root sudo echo "Cron is working"
=============================================

saved the file too. But in every fourth minute of each hour I am not getting any o/p, better to say no o/p at all. What is the problem?

---

