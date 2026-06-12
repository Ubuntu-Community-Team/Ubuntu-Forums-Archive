---
title: "mysql for amarok"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by gacostac on 2007-10-09
Hi 
Can anyone help me set up mysql for amarok in ubuntu 7.4? i tried the following instructions but got an error:

   sudo apt-get install mysql-server mysql-client


now this (replace PASSWORD with your password)

    mysqladmin -u root password PASSWORD

then this

    mysql -p -u root
    CREATE DATABASE amarok;
    USE mysql;
    GRANT ALL ON amarok.* TO amarok@localhost IDENTIFIED BY 'PASSWORD_CHANGE_ME';
    FLUSH PRIVILEGES;


In Amarok, go to settings> configure Amarok
Click Collection

Select MySQL.

Use the following settings:

    Hostname: 127.0.0.1
    Database: amarok
    Port: 3306
    Username: amarok
    Password: Your Password  )

I got stucked in the second step and got :

gacostac@gacostac-desktop:~$ mysqladmin -u root password #####
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

Any help is welcomed

---

### Post by milosz.galazka on 2007-10-09
Run command:
```
ps ax | grep mysql
```
If you get similar output:
```
15890 pts/1    S      0:00 /bin/sh /usr/bin/mysqld_safe
15927 pts/1    Sl     0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
15928 pts/1    S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
15991 pts/1    R+     0:00 grep mysql

```
then it's running...

Or if you get nothing or just:
```
16050 pts/1    R+     0:00 grep mysql
```
then try
```
sudo /etc/init.d/mysql start
```
If you get *command not found* here then check if */usr/bin/mysqld_safe* exists.

My mysql* packages: 
```
milosz@bluebird:~$ dpkg-query -l mysql*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Nazwa          Wersja         Opis
+++-==============-==============-============================================
un  mysql-client   <brak>         (brak dost&#281;pnego opisu)
ii  mysql-client-5 5.0.45-1ubuntu MySQL database client binaries
ii  mysql-common   5.0.45-1ubuntu MySQL database common files
un  mysql-doc-5.0  <brak>         (brak dost&#281;pnego opisu)
ii  mysql-navigato 1.4.2-9        GUI client program for MySQL database server
ii  mysql-server   5.0.45-1ubuntu MySQL database server (meta package dependin
ii  mysql-server-5 5.0.45-1ubuntu MySQL database server binaries

```

It's late so sorry if there is any inconsistency...

---

### Post by gacostac on 2007-10-09
Thanks, here is what i got:
gacostac@gacostac-desktop:~$ ps ax | grep mysql
 1422 pts/0    S+     0:00 grep mysql
 5044 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 5092 ?        Sl     0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 5094 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
gacostac@gacostac-desktop:~$ sudo /etc/init.d/mysql start
Password:
 * Starting MySQL database server mysqld                                 [ OK ] 

It looks different than yours, but when i used the start command i got that OK

What do i do next?

---

### Post by milosz.galazka on 2007-10-09
just follow your procedure :)

---

