---
title: "MythTv Issues"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by WiseguyY2K on 2007-10-28
I tried searching for this issue, but I'm lost.  I installed MythTV frontend / backend from the add / remove program area along with MythTV Control Center.  Well, I tried running Control Center, it asked for my password then did nothing.  So I tried running the backend Setup, well I can't seem to get that to work either...here is a picture of the set up, I think everything looks right 
[[IMG]http://img100.imageshack.us/img100/8036/screenshot1ui6.th.png[/IMG]](http://img100.imageshack.us/my.php?image=screenshot1ui6.png)

So, I tried running the frontend and it shows the same thing it shows when I click on the backend.  So I'm not sure what I'm doing wrong, I followed this [https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop) and this one [https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)
 and I came out with these errors. 

```
john@john-desktop:~$ more /var/log/mythtv/mythbackend.log
2007-10-27 21:49:50.575 Using runtime prefix = /usr
2007-10-27 21:49:50.653 New DB connection, total: 1
2007-10-27 21:49:50.743 Unable to connect to database!
2007-10-27 21:49:50.763 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-10-27 21:49:50.854 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-10-27 21:49:50.948 Failed to init MythContext, exiting.
2007-10-27 21:53:09.828 Using runtime prefix = /usr
2007-10-27 21:53:10.161 New DB connection, total: 1
2007-10-27 21:53:10.328 Unable to connect to database!
2007-10-27 21:53:10.333 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-10-27 21:53:10.439 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-10-27 21:53:10.500 Failed to init MythContext, exiting.
2007-10-27 23:44:09.535 Using runtime prefix = /usr
2007-10-27 23:44:09.786 New DB connection, total: 1
2007-10-27 23:44:12.026 Unable to connect to database!
2007-10-27 23:44:12.052 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-10-27 23:44:12.229 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-10-27 23:44:12.330 Failed to init MythContext, exiting.
2007-10-28 00:11:38.371 Using runtime prefix = /usr
2007-10-28 00:11:38.612 New DB connection, total: 1
2007-10-28 00:11:38.879 Unable to connect to database!
2007-10-28 00:11:38.898 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-10-28 00:11:38.962 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-10-28 00:11:39.019 Failed to init MythContext, exiting.
2007-10-28 00:16:28.511 Using runtime prefix = /usr
2007-10-28 00:16:28.555 New DB connection, total: 1
2007-10-28 00:16:28.564 Unable to connect to database!
2007-10-28 00:16:28.566 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-10-28 00:16:28.626 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-10-28 00:16:28.685 Failed to init MythContext, exiting.
2007-10-28 00:19:12.324 Using runtime prefix = /usr
2007-10-28 00:19:12.356 New DB connection, total: 1
2007-10-28 00:19:12.362 Unable to connect to database!
2007-10-28 00:19:12.363 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-10-28 00:19:12.420 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-10-28 00:19:12.475 Failed to init MythContext, exiting.
2007-10-28 00:22:32.748 Using runtime prefix = /usr
2007-10-28 00:22:32.780 New DB connection, total: 1
2007-10-28 00:22:32.790 Unable to connect to database!
2007-10-28 00:22:32.791 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-10-28 00:22:32.854 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-10-28 00:22:32.913 Failed to init MythContext, exiting.
2007-10-28 00:27:18.235 Using runtime prefix = /usr
2007-10-28 00:27:18.262 New DB connection, total: 1
2007-10-28 00:27:18.273 Unable to connect to database!
2007-10-28 00:27:18.275 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-10-28 00:27:18.341 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-10-28 00:27:18.398 Failed to init MythContext, exiting.
2007-10-28 00:32:13.876 Using runtime prefix = /usr
2007-10-28 00:32:14.125 New DB connection, total: 1
2007-10-28 00:32:14.423 Unable to connect to database!
2007-10-28 00:32:14.461 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-10-28 00:32:14.542 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-10-28 00:32:14.600 Failed to init MythContext, exiting.

```

I'm running 7.10 Gusty, 64 bit.  Not that it might matter but I have a Hauppage WinTV pvr 150

Thank you!  This forum helped solve my other issues such as getting AWN working.

---

### Post by zabzoo on 2007-11-04
THANK YOU FOR A GREAT FORUM 

I am posting in this thread because I too have an issue with the MythTV installation guide located here 

[https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop)

How do you create a "application association" in Firefox for Liinux, like the one required by this link to install MythTV - ???

[http://mythbuntu.org/download/getmythbuntu.php](http://mythbuntu.org/download/getmythbuntu.php)

This is probably not the right post for this but GUTSY ROCKS :guitar:, Thank You  x googleplex.  Everything else went super smooth.

I will start a new thread, because my mythTV is also not working, I will describe my issue there to find assistance.  Thanks.

---

### Post by MrMutch on 2007-11-19
I'm new at both Ubuntu and using the forums.  Has anyone found a solution to WiseguyY2K's issue?  I have been trying to get MythTV running for over a week and I am having exactly the same error.  I've haven't seen a solution and I have tried several 'how to' threads.  If anyone has a solution to this specific problem (Access denied for user 'mythtv'@'localhost' (using password: YES)), I'd really like to know

Thanks.

---

### Post by SgtDude on 2007-11-19
I've run into this one.  It's been a couple of weeks, so I don't remember all the details, but here goes.

The problem is that the password for the user 'mythtv' that's in your backend configuration is the wrong password for the 'mythtv' user.  The other problem is that the 'mythtv' user we're refering to is a user in a mysql database, and not a user on the actual OS, so we can't just reset it's password (or rather, **I** don't know how to reset the password).

The way I fixed it was by re-installing.  If this is an option for you, make sure you make a note of the mysql root password, and the mythtv user password during the installation.

If re-installing isn't an option for you, I'd search the forums for some info on managing mysql users.

Good luck.

---

### Post by zabzoo on 2007-11-20
How i eventually came right was to download MythBuntu -

[http://www.mythbuntu.org/downloads](http://www.mythbuntu.org/downloads)

MythTV already works on there; you can then just add Kubuntu (which is my favourite) or gnome if you need to afterwards and have a working MythTV on Linux.

There are some other difficulties too but at least you know MythTV is confiugred correctly and you can now focus on figuring out how to set the channels and download the XML schedule information (took me about an hour). :)

---

