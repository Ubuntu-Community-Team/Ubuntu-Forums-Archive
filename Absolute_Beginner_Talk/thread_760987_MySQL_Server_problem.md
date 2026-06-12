---
title: "MySQL Server problem"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by latheesan on 2008-04-20
Hello,

I just finished installing mysql5, php5 and apache2 so as a final step, i tried to install phpmyadmin like this :

sudo apt-get install phpmyadmin

It started to download and install it self and towards the end, there was some odd error with mysql. Take a look :

> Unpacking phpmyadmin (from .../phpmyadmin_4%3a2.10.3-1_all.deb) ...
Setting up mysql-server-5.0 (5.0.45-1ubuntu3) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [COLOR="Red"][fail][/COLOR] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Setting up libmcrypt4 (2.5.7-5) ...

Setting up php5-mcrypt (5.2.3-0ubuntu1) ...

Setting up phpmyadmin (4:2.10.3-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@laptop:~#

What does this error means and how can i fix it?

---

### Post by latheesan on 2008-04-20
I even tried to re-install mysql server like this :

sudo apt-get install --reinstall mysql-server

i got the follwoing :

> root@laptop:~# apt-get install --reinstall mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up mysql-server-5.0 (5.0.45-1ubuntu3) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [COLOR="Red"][fail][/COLOR] 
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
root@laptop:~#

---

### Post by castor_fou on 2008-04-24
I am in the exact same situation here.
Anyone to help ?

---

### Post by JB_e on 2008-06-06
I have the same EXACT problem I really don't know what's going on. and apparently there is some problem with ubuntu.security.com

---

### Post by fcser on 2008-06-20
Same error here

---

### Post by K-4U on 2008-07-01
Same problem here!

Please, someone who can help?

---

### Post by unutbu on 2008-07-01
What happens when you run
```

dpkg --configure mysql-server-5.0
```
Please post any output.


The problem is that mysql-server-5.0 has not been fully installed. The last step in the installation is to run the post-installation script, and that script is encountering an error. 
```

root@laptop:~# apt-get install --reinstall mysql-server
...
dpkg: **error processing mysql-server-5.0 (--configure)**:
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
mysql-server depends on mysql-server-5.0; however:
Package mysql-server-5.0 is not configured yet.

```

---

### Post by webofunni on 2008-07-07
Hello,

  Please do the following and paste the results : 

1. Open a terminal and enter the following command 

```
 sudo tail -f /var/log/syslog
```

2. Keep the above window and execute the below command in another window : 

```
sudo /etc/init.d/mysql restart
```

3. Copy and paste the result of the "sudo tail -f /var/log/syslog" command.

---

### Post by heivoll on 2008-07-07
Hi. I've encountered the same problem. Doing what webofunni said gives me this:
```
anders@anders-laptop:~$ sudo tail -f /var/log/syslog
Jul  7 13:09:04 anders-laptop mysqld[12240]: InnoDB: File name ./ibdata1
Jul  7 13:09:04 anders-laptop mysqld[12240]: InnoDB: File operation call: 'open'.
Jul  7 13:09:04 anders-laptop mysqld[12240]: InnoDB: Cannot continue operation.
Jul  7 13:09:04 anders-laptop kernel: [ 1180.166327] audit(1215428944.323:195): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/media/Ekstern/web/xampp/mysql/data/ibdata1" pid=12239 profile="/usr/sbin/mysqld" namespace="default"
Jul  7 13:09:04 anders-laptop mysqld_safe[12248]: ended
Jul  7 13:09:18 anders-laptop /etc/init.d/mysql[12399]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jul  7 13:09:18 anders-laptop /etc/init.d/mysql[12399]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Jul  7 13:09:18 anders-laptop /etc/init.d/mysql[12399]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jul  7 13:09:18 anders-laptop /etc/init.d/mysql[12399]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Jul  7 13:09:18 anders-laptop /etc/init.d/mysql[12399]: 
```

edit: Then it finally hit me that I had pointed the datadir config to a place on an external harddisk running with NTFS filesystem. Changing this back to the original point (/var/lib/mysql) fixed it for me.
So if anyone else just have done the same mistake as me (though it shouldn't be that ordinary of a mistake to do, I'm feeling stupid here :P), here's the answer:

1. Edit MySQL's config file. Open a terminal and write ```
sudo gedit /etc/mysql/my.cnf
``` Then change the datadir variable so line around 47 looks like this: datadir		= /var/lib/mysql
2. Restart MySQL. Run in terminal ```
sudo /etc/init.d/mysql start
```

---

### Post by webofunni on 2008-07-07
Hello heivoll,

  Your Mysql error is related with the InnoDB log files. Mysql failed because it is not able to open the InnoDB log file 'ibdata1'. The InnoDB log files resides in the Mysql data directory and as you said Mysql failed because you changed the data directory to another file system. But I don't think this is the problem with others. Waiting for their reply :-)

---

