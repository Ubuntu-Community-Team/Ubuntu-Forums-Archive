---
title: "Installing a LAMP setup"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Corvinis on 2007-06-04
Hey there,

I'm trying to setup a lamp server.... but it stops at the last command in the code below:

```

gksudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-mpm-prefork apache2-utils apache2.2-common libapr1 libaprutil1
  libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl
  libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server-5.0
  php5-common
Suggested packages:
  php-pear dbishell libcompress-zlib-perl tinyca
Recommended packages:
  mailx
The following NEW packages will be installed:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common
  libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl
  libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0
  mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql
0 upgraded, 19 newly installed, 0 to remove and 0 not upgraded.
Need to get 39.4MB/40.9MB of archives.
After unpacking 106MB of additional disk space will be used.
Do you want to continue [Y/n]? Y

```


what's causing this?

Thanks

Corvinis

---

### Post by Cypher on 2007-06-04
You were prompted for the root password after that command? If so, try replace the "gksudo" with "sudo" and see if the results vary..

---

### Post by Corvinis on 2007-06-04
k thanks it's installing now

---

### Post by Cypher on 2007-06-04
You're welcome..good luck with the rest..

---

