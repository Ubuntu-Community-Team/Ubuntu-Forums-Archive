---
title: "LAMP on Desktop installation (not the server)"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by HEMOglobina on 2006-11-23
I've downloaded and installed the Desktop version of Ubuntu on my machine but now I want to have LAMP up and running on it (just for in house development, not to be accessible to the outside world).
I dont want to reinstall Ubuntu just and get the Server edition because I already have lots of things configured.
Is there an easy way to install LAMP or I will have to go the hard way and install package by package and tie them up?
I've tried to "google" on this, but every solution I've found was regarding the installation of Ubuntu Server.

Thank you for your help,
HEMOglobina

---

### Post by edmund on 2006-11-23
If you install apache and php5, php "just works" on Apache with no further configuration required.

---

### Post by NotJustANewbie on 2006-11-23
If you want mysql to work as well, you need to intall the mysql-php and mysql packages.

This should integrate L,A,M,P together

---

### Post by Circus-Killer on 2006-11-23
to install a lamp server on an ubuntu desktop just issue the following command:

>  $ sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

for more details and info have a read through [this]("https://help.ubuntu.com/community/ApacheMySQLPHP") page.

---

### Post by HEMOglobina on 2006-11-23
Thank you very much Circus-Killer. It worked like a charm ;)

---

