---
title: "Can't install mysql server"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Nutopia on 2008-01-20
I ran:  sudo apt-get install mysql-server-5.0

and before it ended I got:

Setting up mysql-server-5.0 (5.0.45-1ubuntu3) ...
 * Stopping MySQL database server mysqld                                                                                     [ OK ] 
 * Starting MySQL database server mysqld                                                                                     [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any idea what it means?

---

### Post by gate on 2008-01-21
Looks like dpkg failed while trying to start up the MySQL Daemon. 
  You should have a MySQL log file, look in /var/log/mysql.err

---

### Post by Majorix on 2008-01-21
I don't think he has that log - MySQL didn't install.

You would go a long way if you were to install MySQL along with Apache and PHP through Synaptic. Click Edit > Mark Packages by Task and select "LAMP Server". That will handle all the dependencies etc for you.

---

### Post by indytim on 2008-01-21
Another way to install the entire package is:
```

$tasksel

```

IndyTim

---

### Post by Majorix on 2008-01-21
Yes that's a terminal shortcut that does pretty much the same. But I always tend to think GUI is easier, though it is a matter of taste :)

---

### Post by Nutopia on 2008-01-21
Ok... thanks for everyone's help! That is a much easier way. However, it looks like I have the same problem even after I "Marked by task"...

Here is the error that happens during the install:
E: mysql-server-5.0: subprocess post-installation script returned error exit status 1
E: mysql-server: dependency problems - leaving unconfigured

Unfortunately I can't copy the install log. It says:

Errors were encountered while processing:
mysql-server-5.0
mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Stopping mysql database server mysqld
...done.
Starting mysql database server mysqld
...fail!
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
mysql-server depends on mysql-server 5.0; however:
Package mysql-server-5.0 is not configured yet.


So those last lines seem to say something... but I would assume that installing the entire LAMP package would work without issue, would it not?

---

### Post by Nutopia on 2008-01-21
It looks to me like the main problem is the mysql-server-5.0 install fails:
E: mysql-server-5.0: subprocess post-installation script returned error exit status 1

Which then causes the dependency issue with mysql-server.

Any ideas how to correct this? Should I just wipe out Ubuntu totally and start again a different way? Isn't there some way to configure LAMP during the install?

---

### Post by gate on 2008-01-22
It looks as though mysql is installed, it just isn't configured because dpkg couldn't start it up. You need to figure out why mysql won't start up, so no matter what front end you select mysql from, apt will still not finish installing it. 
   Check for log files! see what files are in /var/log/   that start with mysql   (mysql.err) and paste them here.
 

    if all else fails, you can clean up your first attempt at mysql and start over with
 
     sudo aptitude purge mysql mysql-server-5.0
     sudo apt-get autoremove

---

