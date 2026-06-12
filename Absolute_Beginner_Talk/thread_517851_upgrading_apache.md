---
title: "upgrading apache?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by hc2995 on 2007-08-05
i noticed that when i got to 127.0.0.1 the apache version is Apache/2.0.55 (Ubuntu) I am using ubuntu 6.06 and wanted to know if it was possible to upgrade to apache 2.2.4? Also, where is the configuration file for this apache (i guess it came preinstalled, i didnt install it) Im kinda a noob at ubuntu and linux all together (iv used it, but now i plan to use it as my primary system) And yes, i know im using an out dated version of ubuntu, but, this version is the fastest on my system, dont know why.

---

### Post by avik on 2007-08-05
Actually, 6.06 isn't outdated, since it is an LTS version.  Anyway, it seems Apache 2.2 hasn't been backported to Dapper (it's there on Feisty, and maybe on Edgy as well), but I found [this guide to compiling it yourself]("http://davidwinter.me.uk/articles/2006/10/17/building-apache-22-from-source-for-ubuntu-dapper/").  Hope that helps.

Also, I believe the configuration files are in /etc/apache2/.

---

### Post by hc2995 on 2007-08-05
I know support for dapper is extened to like 2008, but i will most likely upgrade some day :P

---

### Post by avik on 2007-08-05
Actually, the support is extended until 200**9**.  Anyway, did you get everything worked out?

---

### Post by hc2995 on 2007-08-05
Iv installed it fine, but i have a problem with my config file, here is what the termianl shows:

```

admin@nautilus:~$ sudo /usr/local/apache2/bin/apachectl start
httpd: Syntax error on line 86 of /usr/local/apache2/conf/httpd.conf: Cannot load /usr/local/apache2/modules/mod_proxy_http.so into server: /usr/local/apache2/modules/mod_proxy_http.so: undefined symbol: ap_proxy_location_reverse_map

```

---

### Post by hc2995 on 2007-08-05
Anyone

---

### Post by avik on 2007-08-05
Try commenting out line 86 of your httpd.conf file (put a # at the very beginning of the line).  That might be a temporary solution, but I don't know how to fix it completely.

---

