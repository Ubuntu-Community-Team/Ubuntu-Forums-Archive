---
title: "php4 and php5 is installed but php4 gets started"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by byenary on 2007-05-16
Hello, i have installed both php4 and php5 on a dapper machine but php 4 is running but i want to migrate to php5, how should i do this in a safe manner ?

Thx

---

### Post by Bachstelze on 2007-05-16
Why don't you just remove PHP 4 if you don't need it anymore ?

---

### Post by byenary on 2007-05-16
I could try that but since its running on server wich is in use at the company i can't take the risk ending up with nothing...
And it don't think removing php4 makes php5 get started instead...

---

### Post by Bachstelze on 2007-05-16
Obviously, you'll need to edit your Apache config file so it loads php5 instead of php4. Just do

```
sudo nano -w /etc/apache2/apache2.conf
```

And replace all occurences of php4 with php5.

---

### Post by byenary on 2007-05-16
thx for your assistance but  my conf files does not seem to  have either php4 or php5 occurences ...

---

### Post by Bachstelze on 2007-05-16
Hmm, how about

```
ls /etc/apache2/
```

does it have two subdirs called mods-available and mods-enabled in it ?

---

### Post by byenary on 2007-05-16
Yes, what does that mean ?

root@Backupsrv:/etc/apache2# ls
apache2.bu    apache2.conf.save    apache2.conf.save.2  conf.d   httpd.conf  mods-available  ports.conf  sites-available  ssl
apache2.conf  apache2.conf.save.1  apache2.conf.save.3  envvars  magic       mods-enabled    README      sites-enabled
root@Backupsrv:/etc/apache2# cd mods-enabled/
root@Backupsrv:/etc/apache2/mods-enabled# ls
cgi.load  php5.conf  php5.load  userdir.conf  userdir.load
root@Backupsrv:/etc/apache2/mods-enabled# cd ..
root@Backupsrv:/etc/apache2# cd mods-available/
root@Backupsrv:/etc/apache2/mods-available# ls
actions.load      auth_ldap.load  cgi.load      disk_cache.load  imap.load       mime_magic.conf  proxy_connect.load  speling.load    userdir.conf
asis.load         cache.load      dav_fs.conf   expires.load     include.load    mime_magic.load  proxy_ftp.load      ssl.conf        userdir.load
auth_anon.load    cern_meta.load  dav_fs.load   ext_filter.load  info.load       php5.conf        proxy_http.load     ssl.load        usertrack.load
auth_dbm.load     cgid.conf       dav.load      file_cache.load  ldap.load       php5.load        proxy.load          suexec.load     vhost_alias.load
auth_digest.load  cgid.load       deflate.load  headers.load     mem_cache.load  proxy.conf       rewrite.load        unique_id.load
root@Backupsrv:/etc/apache2/mods-available#

---

### Post by Bachstelze on 2007-05-16
That's weird, you have php5 in mods-enabled... Are you sure your Apache still loads PHP 4 ?

---

### Post by byenary on 2007-05-16
yes i am,
root@Backupsrv:~# cd /etc/init.d
root@Backupsrv:/etc/init.d# ./apache2 restart
 * Forcing reload of web server  (Apache2)...                            [ ok ]
root@Backupsrv:/etc/init.d# mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 264 to server version: 4.0.24_Debian-10ubuntu2.3-log
Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> SELECT version()
    -> ;
+-------------------------------+
| version()                     |
+-------------------------------+
| 4.0.24_Debian-10ubuntu2.3-log |
+-------------------------------+
1 row in set (0.00 sec)

---

### Post by Bachstelze on 2007-05-16
This is your MySQL version, not your PHP version...

---

### Post by byenary on 2007-05-16
Im am deeply ashamed :oops: :oops: ,

I have 5.0.5-2 running after all, thing is I used a function file_get_contents() on an other server wich works fine but on the the server the one i was messing with the versions he says to have to many arguments.
Hou should i than upgrade to 5.1.2  :)

---

### Post by byenary on 2007-05-16
its like a friday today..

---

### Post by Bachstelze on 2007-05-16
Just upgrade the usual way :

```
sudo apt-get update
sudo apt-get dist-upgrade
```

That should give you PHP 5.1.2

---

### Post by az on 2007-05-16
> **byenary said:**
> Im am deeply ashamed :oops: :oops: ,

I have 5.0.5-2 running after all, thing is I used a function file_get_contents() on an other server wich works fine but on the the server the one i was messing with the versions he says to have to many arguments.
Hou should i than upgrade to 5.1.2  :)

sudo apt-get install libapache2-mod-php5

---

### Post by Bachstelze on 2007-05-16
If he has PHP 5.0, I'd assume php5 is already installed...

---

### Post by az on 2007-05-16
> **HymnToLife said:**
> If he has PHP 5.0, I'd assume php5 is already installed...

You can have both php4 and php5 installed at the same time.  The libapache2-mod-phpX package determines which one is used by apache.  It is possible to have php5 and apache2 installed without the libapache2-mod-php5 module installed, and that is usually the source of the problem.

---

### Post by byenary on 2007-05-17
thx you both, Ill give this a shot on monday its a holiday today over here :)

---

### Post by adza on 2007-05-17
errr... this might sound like a crazy idea, but if you are planning on doing this on your commercial system, what was the result when you tried this on your DEV machine?

---

### Post by byenary on 2007-05-21
root@Backupsrv:~#  sudo aptitude search libapache2-mod-php
p   libapache2-mod-php4                           - server-side, HTML-embedded scripting language (apache 2.
iB  libapache2-mod-php5                           - server-side, HTML-embedded scripting language (apache 2.
root@Backupsrv:~#


Still not working, whats iB ?

---

