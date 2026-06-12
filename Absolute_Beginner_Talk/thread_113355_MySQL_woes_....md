---
title: "MySQL woes ..."
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by wannabelinuxconvert on 2006-01-06
Hi,

I've just used the command 

```
sudo apt-get install mysql-server
```

And half way through the installation, I was given the Postfix configuration screen, as I had not asked to install Postfix, I selected the no-configuration option and the installation carried on. Except when it tried to start the server I get the message

```

Unpacking mysql-server (from .../mysql-server_4.0.24-10ubuntu2_powerpc.deb) ...
Setting up mysql-server (4.0.24-10ubuntu2) ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

```

I found a similar post on the forum advising to do a 

```

sudo apt-get --purge remove mysql-server
sudo apt-get install mysql-server

```

Which seemed to fix the other users problem, so I gave it a go and got 

```

sudo apt-get --purge remove mysql-server
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  mysql-server*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 9105kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 97880 files and directories currently installed.)
Removing mysql-server ...
Stopping MySQL database server: mysqld.
Purging configuration files for mysql-server ...
mic@ubuntu:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  mysql-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3664kB of archives.
After unpacking 9105kB of additional disk space will be used.

Preconfiguring packages ...
send-mail: fatal: open /etc/postfix/main.cf: No such file or directory
Can't send mail: sendmail process failed with error code 1
Selecting previously deselected package mysql-server.
(Reading database ... 97713 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_4.0.24-10ubuntu2_powerpc.deb) ...
Setting up mysql-server (4.0.24-10ubuntu2) ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

```

So have the same problem again.

I checked the syslog as advised and found the following

```

InnoDB: No valid checkpoint found.
InnoDB: If this error appears when you are creating an InnoDB database,
InnoDB: the problem may be that during an earlier attempt you managed
InnoDB: to create the InnoDB data files, but log file creation failed.
InnoDB: If that is the case, please refer to
InnoDB: http://dev.mysql.com/doc/mysql/en/Error_creating_InnoDB.html
060105 22:24:11 Can't init databases
060105 22:24:11 Aborting
060105 22:24:11  InnoDB: Warning: shutting down a not properly started
                 InnoDB: or created database!
060105 22:24:11 mysqld: Shutdown Complete

```

Can anyone help with this error as I really need to get MySQL up and running.

Also, can anyone tell me how to completely remove the installation and start again so I get the postfix config screen as maybe this is causing the problem !? When I've removed and and re-installed it has never prompted again.

I'm using Ubuntu 5.10 on a MacMini

All help will be greatly appreciated.

Thanks

Mic

---

