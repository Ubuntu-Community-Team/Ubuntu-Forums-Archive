---
title: "Services"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by lynxus on 2006-09-11
hey guys, Ive recently installed apache, however i cannot see the service ir at least start it..

I try 

service apache start 

but it says bad command, Then i try sudo service apache start .
Same problem ?

wheres the service app gone ?


gsmart@gsmart-laptop:~$ service apache start
bash: service: command not found
gsmart@gsmart-laptop:~$ sudo service apache start
sudo: service: command not found
gsmart@gsmart-laptop:~$ #

---

### Post by monktbd on 2006-09-11
instead of service you can also write:

/etc/init.d/

so e.g.
> 
/etc/init.d/apache start

---

### Post by jordanmthomas on 2006-09-11
If you installed apache2, you have to put apache2, not just apache.
This could be your problem as well.

---

### Post by lynxus on 2006-09-11
> **jordanmthomas said:**
> If you installed apache2, you have to put apache2, not just apache.
This could be your problem as well.


tried both ways.

When i install apache2 from the synaptec thing it doesnt seem to install much..

I do a Locate apache2 and cant find any httpd.conf file etc..

---

### Post by jordanmthomas on 2006-09-11
Does the folder 
```
/usr/share/apache2
```
exist?  If not, does 
```
/usr/share/apache
```
exist?

---

