---
title: "MythTV + MySQL issue"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by Jarnz on 2006-08-26
I know many people have had problems with MythTV and MySQL working together, and I have spent a day searching these forums, MythTV+MySQL documentation and general google searching and I cannot find anything that helps me with my issue.

I've install MythTV 0.19 to the point of running mythtv-setup to configure the backend. MySQL5 is installed and for what I know, its configured. I've altered the /etc/mysql/my.cnf file to have the PCs IP address. The proper database and users are configured automatically by MythTV when adding the mc.sql file into MySQL.

With al this, everytime I start mythtv-setup, it cannot conntect to the database. I've checked the settings when the setup starts and they are correct. I believe the issue is with MySQL (I'm just guessing really) but I have no idea where to start.

Help would be very greatful. Thank you

---

### Post by v1ct0r on 2006-08-26
Start with these : 
[http://www.mythtv.org/docs/mythtv-HOWTO.html#toc6](http://www.mythtv.org/docs/mythtv-HOWTO.html#toc6)
[http://www.abarbaccia.com/content/view/17/32/](http://www.abarbaccia.com/content/view/17/32/)
[http://www.ubuntu-mythtv.blogspot.com/](http://www.ubuntu-mythtv.blogspot.com/)
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

...and so on. Hope those links are helpful in any way.

---

### Post by Jarnz on 2006-08-26
I followed the MythTV documentation.

I've spent this morning getting MySQL database on my other computer configured. ran mythtv-setup, put in the database details, and it still cant find the database. I know this database is working because its on the net with php and apache.

I re-compiled MythTV and installed again, and it just cant find the database on either PC. I dont know what I'm doing wrong as nothing in many walkthroughs suggest I'm missing something.

```

2006-08-27 11:32:37.520 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-08-27 11:32:37.576 Database not open while trying to load setting: Language2006-08-27 11:32:37.577 Unable to connect to database!
2006-08-27 11:32:37.577 No error type from QSqlError?  Strange...
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-08-27 11:32:37.632 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-08-27 11:32:37.688 Database not open while trying to save setting: Language2006-08-27 11:32:37.689 Unable to connect to database!
2006-08-27 11:32:37.689 No error type from QSqlError?  Strange...
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-08-27 11:32:37.744 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-08-27 11:32:40.504 Unable to connect to database!
2006-08-27 11:32:40.504 No error type from QSqlError?  Strange...
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-08-27 11:32:40.560 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-08-27 11:32:40.612 Failed to init MythContext, exiting.

```

Just a small snippet of whats coming up when I run mythtv-setup

---

### Post by tech9 on 2008-01-04
sounds like you and I have the same issue

---

### Post by giest on 2008-01-07
I got the answer from [this]("http://ubuntuforums.org/showthread.php?p=4092747") thread.

Try blocking out the "bind-address" line below.  That allows mysql connections from non-localhost clients.

```

# /etc/mysql/my.cnf
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
# bind-address		= 127.0.0.1
```

That was my problem


OR If you are running an older version of mysql, you may need to block out 'skip-networking'

```

#/etc/mysql/my.cnf
# skip-networking
```

Hope that helps.

---

