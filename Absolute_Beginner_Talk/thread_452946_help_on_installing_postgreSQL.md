---
title: "help on installing postgreSQL"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-05-23
need help on instlaling postgre SQL plz help
```
zerobinary@zerobinary:~$ sudo apt-get install postgresql-8.2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
postgresql-8.2 is already the newest version.
postgresql-8.2 set to manual installed.
The following packages were automatically installed and are no longer required:
  artsbuilder python-kiwi libgtk-jni libpcrecpp0 libcairo-java
  libbluetooth2-dev libusb-dev librpcsecgss2 libjasper-runtime libgmp3c2
  libxml++2.6c2a libglib-java docker python-setuptools libpq4 gazpacho
  libgconfmm-2.6-1c2 mkvtoolnix libswt3.2-gtk-jni libimlib2 multisync
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up postgresql-8.2 (8.2.4-1~edgy1) ...
 * Starting PostgreSQL 8.2 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2007-05-23 18:06:52 PDT LOG:  could not load root certificate file "root.crt": no SSL error reported
2007-05-23 18:06:52 PDT DETAIL:  Will not verify client certificates.
2007-05-23 18:06:53 PDT LOG:  could not translate host name "localhost", service "5432" to address: Name or service not known
2007-05-23 18:06:53 PDT WARNING:  could not create listen socket for "localhost"
2007-05-23 18:06:53 PDT FATAL:  could not create any TCP/IP sockets
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.2, action "start" failed.
dpkg: error processing postgresql-8.2 (--configure):

```

---

