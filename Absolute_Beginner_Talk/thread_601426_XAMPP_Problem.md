---
title: "XAMPP Problem"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Zacharias on 2007-11-03
Hi guys 
i have already installed XAMPP according to XAMPP document of this site, however when i tried to run sudo /opt/lampp/lampp start command 

i took the fallowing error

Starting XAMPP for Linux 1.5.3a...
XAMPP: Another web server daemon is already running.
/opt/lampp/bin/mysql.server: 84: source: not found
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
 /opt/lampp/bin/mysql.server: 334: log_success_msg: not found

how can i fix that ?

The other question is about mpeg4 video format, cant watch it.. i can watch all the formats except mpeg4. how can fix that also ?

thanks a lot

---

### Post by kosmic on 2007-11-03
See this message ??

XAMPP: Another web server daemon is already running.

It means that you already have a webserver listening in that port...

Probably you already have Apache installed and tried to install XAMPP and start a second instance of xampp.

do a "netstat -lunt" a post where the results....

---

### Post by escobar_ on 2007-11-03
Try stopping Apache first (if you have one running)

sudo /etc/init.d/apache stop

Then start XAMPP.

---

