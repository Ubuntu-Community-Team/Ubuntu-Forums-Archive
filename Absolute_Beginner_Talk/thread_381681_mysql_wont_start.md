---
title: "mysql wont start"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Kossu on 2007-03-11
Hello,

Been trying to get mysql to work for the past day without success.

basically it wont start, tried reinstalling and what not, heres the errors and some info.

```

dpkg -l | grep mysql
ii  libdbd-mysql-perl                      3.0006-1                             A Perl5 database interface to the MySQL data
ii  libmysqlclient14                       4.1.15-1ubuntu5                      mysql database client library
ii  libmysqlclient15off                    5.0.24a-9                            mysql database client library
ii  libqt3-mt-mysql                        3.3.6-3ubuntu3                       MySQL database driver for Qt3 (Threaded)
ii  mysql-client                           5.0.24a-9                            mysql database client (current version)
ii  mysql-client-5.0                       5.0.24a-9                            mysql database client binaries
ii  mysql-common                           5.0.24a-9                            mysql database common files (e.g. /etc/mysql
iF  mysql-server-5.0                       5.0.24a-9                            mysql database server binaries
ii  python-mysqldb                         1.2.1-p2-4ubuntu2                    A Python interface to MySQL

```

```

sudo aptitude install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  mysql-server 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/39.5kB of archives. After unpacking 69.6kB will be used.
Writing extended state information... Done
Selecting previously deselected package mysql-server.
(Reading database ... 114036 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.0.24a-9_all.deb) ...
Setting up mysql-server-5.0 (5.0.24a-9) ...
 * Stopping MySQL database server mysqld                                           [ ok ] 
 * Starting MySQL database server mysqld                                           [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.0 (5.0.24a-9) ...
 * Stopping MySQL database server mysqld                                           [ ok ] 
 * Starting MySQL database server mysqld                                           [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server

```

Any help is greatly appreciated.

---

### Post by Arby on 2007-03-14
Hi.

I'm no expert on mysql. Having looked at your error messages I did a bit of searching. I found this thread [http://ubuntuforums.org/showthread.php?t=339505](http://ubuntuforums.org/showthread.php?t=339505) which reports the same problem you have. I think you need to look closely at the file /etc/mysql/my.cnf The two likely problems seem to be an InnoDB memory error or if you have recently changed over to wireless networking. 

I've attached the my.cnf file from my system which currently has a working mysql 5.0 install on it. You can use this to compare against. I strongly recommend that you backup your existing my.cnf file to another name and location before you make any changes so that you can fall back if need be. If you get stuck you could post your my.cnf file here and people can try to see whats wrong

hope that helps

Arby

---

