---
title: "mysql tips"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2007-04-26
I just installed mysql and can not connect to root?
It's a brand new install with nothing chagned. I checked the System > Administration > Services and it 's running, but any attempt to connect doesn't allow.

I also found the /etc/mysql/my.cnf to ensure I was using the correct root password and that does't work either? Oh and I tried to reinstall too?

Totally LOST!:confused:

---

### Post by Seisen on 2007-04-26
Did you setup a user for MySQL?

---

### Post by cjnkns on 2007-04-26
Umm no i assumed that i could connect as root without having any other users...

---

### Post by Seisen on 2007-04-26
I'm wrong you don't have to add a user account, try accessing it with root but don't put a password in and see if it works.

---

### Post by ottawa on 2007-04-26
I just went through this and struggled for 2 days to set the root password. all of the info I found wasn't working for me. I have mysql on edgy server installed and to get the root password set I had to use the following

mysql -uroot -pyour-own-password-here mysql

Please not that there are NO SPACES between -u & root and the same for -p your-password-here

This was the ONLY way I got it to work.

msql -u root password your-own-password  

didn't work. I got Access denied.....error message.
Hope that saves you a lot of time and headaches.
 
ottawa

---

### Post by cjnkns on 2007-04-27
Great thanks for the info I will certainly try that.
Right after I get mysql installed..

I attempted to uninstall it and re-install thinking that might be the easiest route to take and I get the following error message...

E: mysql-server-5.0: subprocess post-installation script returned error exit status 1
E: mysql-server: dependency problems - leaving unconfigured

A package failed to install. Trying to recover:
Settup up mysql-server-5.0
/var/lib/dpkg/ingo/mysql-server-t.0.postint: line 143: /etc/mysql/conf.d/old_passwords.cnf: No such file or directory
dpkg: error process mysql-server-5.0 (--configure):
dpkg:dependency problems prevent configuration of mysql-server:
mysql-server depends on mysql-server-5.0 however:
Package mysql-server-t.0 is not configured yet:
dpkg:error processing mysql-server
dependency problems - leaving unconfigured

---

### Post by aktiwers on 2007-04-27
By default Root dont have no password.. so this should work:
```
mysql -u root
```

---

### Post by ottawa on 2007-04-27
to actiwers

and exactly **this code didn't work** for me in edgy server 6.10. I struggled for 2 days with that and could ONLY set the password with 

mysql -uroot -pmypassowrd mysql

as described in my above post

ottawa

---

### Post by darkworld on 2007-05-02
a very useful page. [http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html]("http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html")

---

