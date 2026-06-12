---
title: "selective update strategy..."
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by huggy77 on 2006-08-13
LINUX SEMI-NOOB ON DAPPER DRAKE

basically trying to mimic my godaddy hosting environment...  I need to keep 

apache: 1.3
mysql: 4.0.24

running on my dapper drake box...  is there anyway to make sure that if i run my updates via apt-get that i dont update those 2 programs... Should i use another updating tool?

LOVING UBUNTU - I EVEN PUT IT ON MY GRANDMOTHERS BOX....

thanks!

---

### Post by ThrobbingBrain66 on 2006-08-13
if you use synaptic to update, you can mark the packages to not be updated.   i run kubuntu and adept, so i'm not sure where the option to do this is, but im sure someone else will be able to fill in the details.

---

### Post by az on 2006-08-13
> **huggy77 said:**
> LINUX SEMI-NOOB ON DAPPER DRAKE

basically trying to mimic my godaddy hosting environment...  I need to keep 

apache: 1.3
mysql: 4.0.24

running on my dapper drake box...  is there anyway to make sure that if i run my updates via apt-get that i dont update those 2 programs... 

You do want to update those packages.  But that does not mean that one day, apache 1.3 will be replaced by apache2.  Not at all.

for example:
apache (1.3.34-2)
and apache (1.3.34-3) are two different versions of the same package.

apache2 (2.0.55-4)
and apache2 (2.0.55-5) are two different version of the same package.  apache and apache2 are two completely different packages.  Updating apache may bring you from version 1.3.34-2 to 1.3.34-3, but it will never install apache2.

What it means is that the apache1.3 package may get security patches and updates, and you still want to get those.  The same goes for mysql4.  You do not want to pin (put on hold) those package version.

---

### Post by huggy77 on 2006-08-15
gotcha.... i just got my cf and mysql talking nicely to each other - i dont want to BLOW it sky high

---

### Post by chonger on 2006-08-15
I think this is the article you are looking for.

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

> You can "pin" the version you have installed so that it will not be upgraded.



Its targeted for Debian, but should apply for Ubuntu as well.

---

