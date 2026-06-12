---
title: "mythtv"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by stoli150 on 2007-06-15
Wich forum would I post a myth tv  question?

Its heres a some of the log file

mike@mike-roomdesktop:~$ more /var/log/mythtv/mythbackend.log
2007-06-14 22:48:35.091 Using runtime prefix = /usr
2007-06-14 22:48:35.360 New DB connection, total: 1
2007-06-14 22:48:35.423 Unable to connect to database!
2007-06-14 22:48:35.440 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'
 (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-06-14 22:48:35.886 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-06-14 22:48:36.046 Failed to init MythContext, exiting.
2007-06-14 22:53:59.703 Using runtime prefix = /usr
2007-06-14 22:54:00.669 New DB connection, total: 1
2007-06-14 22:54:00.894 Unable to connect to database!
2007-06-14 22:54:01.046 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:

---

### Post by reclusivemonkey on 2007-06-15
I would think the "Multimedia and Video" section would be the most appropriate. If you don't get any joy there, then you can always ask on the MythTV forums directly, and there is a MythTV IRC channel for ubuntu; #ubuntu-mythtv. HTH

---

