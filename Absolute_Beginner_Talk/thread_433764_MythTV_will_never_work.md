---
title: "MythTV will never work"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by alwaysthenoob on 2007-05-05
I've been trying to get this thing running for weeks now, I tried it a few months ago and gave up but have tried again and STILL get the same problems.... it just wont work, no matter what distribution I use.

It keeps on about "Database Schema upgrade FAILED, unlocking", my log file is below.  If anyone could help it would be greatly appreciated because I'm at my witts end with this.  I've followed every single how-to there is out there and always come back to this error which no one else ever seems to have !

2007-05-05 14:16:15.986 Using runtime prefix = /usr
2007-05-05 14:16:16.264 New DB connection, total: 1
2007-05-05 14:16:16.295 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:16:16.346 Current Schema Version: 
2007-05-05 14:16:16.401 Newest Schema Version : 1160
2007-05-05 14:16:16.731 New DB connection, total: 2
2007-05-05 14:16:16.737 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:16:16.746 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-05-05 14:16:16.754 New DB connection, total: 3
2007-05-05 14:16:16.756 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:16:16.758 Inserting MythTV initial database information.
2007-05-05 14:16:16.760 New DB connection, total: 4
2007-05-05 14:16:16.762 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:16:16.763 Upgrading to schema version 1112
2007-05-05 14:16:16.815 DB Error (Performing database upgrade): 
Query was: CREATE TABLE IF NOT EXISTS codecparams (  profile int(10) unsigned NOT NULL default '0',  name varchar(128) NOT NULL default '',  value varchar(128) default NULL,  PRIMARY KEY  (profile,name)); 
Error was: Driver error was [2/2013]:
QMYSQL3: Unable to execute query
Database error was:
Lost connection to MySQL server during query
 
new version: 1112
2007-05-05 14:16:16.824 Database Schema upgrade FAILED, unlocking.
2007-05-05 14:16:16.825 Couldn't upgrade database to new schema
2007-05-05 14:38:12.496 Using runtime prefix = /usr
2007-05-05 14:38:12.526 New DB connection, total: 1
2007-05-05 14:38:12.532 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:38:12.535 Current Schema Version: 
2007-05-05 14:38:12.536 Newest Schema Version : 1160
2007-05-05 14:38:12.619 New DB connection, total: 2
2007-05-05 14:38:12.620 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:38:12.621 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-05-05 14:38:12.623 New DB connection, total: 3
2007-05-05 14:38:12.624 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:38:12.626 Told to create a NEW database schema, but the database
already has 5 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-05-05 14:38:12.628 Database Schema upgrade FAILED, unlocking.
2007-05-05 14:38:12.629 Couldn't upgrade database to new schema
2007-05-05 14:44:08.959 Using runtime prefix = /usr
2007-05-05 14:44:08.994 New DB connection, total: 1
2007-05-05 14:44:09.084 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:44:09.087 Current Schema Version: 
2007-05-05 14:44:09.088 Newest Schema Version : 1160
2007-05-05 14:44:09.091 New DB connection, total: 2
2007-05-05 14:44:09.092 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:44:09.093 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-05-05 14:44:09.095 New DB connection, total: 3
2007-05-05 14:44:09.096 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:44:09.098 Told to create a NEW database schema, but the database
already has 5 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-05-05 14:44:09.099 Database Schema upgrade FAILED, unlocking.
2007-05-05 14:44:09.100 Couldn't upgrade database to new schema
2007-05-05 14:47:32.828 Using runtime prefix = /usr
2007-05-05 14:47:32.943 New DB connection, total: 1
2007-05-05 14:47:32.949 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:47:32.952 Current Schema Version: 
2007-05-05 14:47:32.954 Newest Schema Version : 1160
2007-05-05 14:47:32.956 New DB connection, total: 2
2007-05-05 14:47:32.957 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:47:32.959 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-05-05 14:47:32.960 New DB connection, total: 3
2007-05-05 14:47:32.962 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:47:32.964 Told to create a NEW database schema, but the database
already has 5 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-05-05 14:47:32.965 Database Schema upgrade FAILED, unlocking.
2007-05-05 14:47:32.966 Couldn't upgrade database to new schema
2007-05-05 14:57:06.469 Using runtime prefix = /usr
2007-05-05 14:57:06.859 New DB connection, total: 1
2007-05-05 14:57:07.082 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:57:07.391 Current Schema Version: 
2007-05-05 14:57:07.481 Newest Schema Version : 1160
2007-05-05 14:57:07.641 New DB connection, total: 2
2007-05-05 14:57:07.761 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:57:07.985 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-05-05 14:57:08.120 New DB connection, total: 3
2007-05-05 14:57:08.324 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:57:08.700 Told to create a NEW database schema, but the database
already has 5 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-05-05 14:57:08.772 Database Schema upgrade FAILED, unlocking.
2007-05-05 14:57:08.976 Couldn't upgrade database to new schema
2007-05-05 14:58:56.613 Using runtime prefix = /usr
2007-05-05 14:58:56.640 New DB connection, total: 1
2007-05-05 14:58:56.646 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:58:56.649 Current Schema Version: 
2007-05-05 14:58:56.651 Newest Schema Version : 1160
2007-05-05 14:58:56.653 New DB connection, total: 2
2007-05-05 14:58:56.654 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:58:56.656 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-05-05 14:58:56.657 New DB connection, total: 3
2007-05-05 14:58:56.659 Connected to database 'mythconverg' at host: localhost
2007-05-05 14:58:56.661 Told to create a NEW database schema, but the database
already has 5 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-05-05 14:58:56.662 Database Schema upgrade FAILED, unlocking.
2007-05-05 14:58:56.663 Couldn't upgrade database to new schema
2007-05-05 15:04:07.407 Using runtime prefix = /usr
2007-05-05 15:04:07.438 New DB connection, total: 1
2007-05-05 15:04:07.444 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:04:07.447 Current Schema Version: 
2007-05-05 15:04:07.448 Newest Schema Version : 1160
2007-05-05 15:04:07.450 New DB connection, total: 2
2007-05-05 15:04:07.451 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:04:07.453 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-05-05 15:04:07.454 New DB connection, total: 3
2007-05-05 15:04:07.456 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:04:07.457 Told to create a NEW database schema, but the database
already has 5 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-05-05 15:04:07.458 Database Schema upgrade FAILED, unlocking.
2007-05-05 15:04:07.459 Couldn't upgrade database to new schema
2007-05-05 15:05:19.290 Using runtime prefix = /usr
2007-05-05 15:05:19.321 New DB connection, total: 1
2007-05-05 15:05:19.326 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:05:19.329 Current Schema Version: 
2007-05-05 15:05:19.331 Newest Schema Version : 1160
2007-05-05 15:05:19.333 New DB connection, total: 2
2007-05-05 15:05:19.334 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:05:19.336 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-05-05 15:05:19.337 New DB connection, total: 3
2007-05-05 15:05:19.338 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:05:19.340 Told to create a NEW database schema, but the database
already has 5 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-05-05 15:05:19.341 Database Schema upgrade FAILED, unlocking.
2007-05-05 15:05:19.343 Couldn't upgrade database to new schema
2007-05-05 15:06:48.316 Using runtime prefix = /usr
2007-05-05 15:06:48.344 New DB connection, total: 1
2007-05-05 15:06:48.351 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:06:48.354 Current Schema Version: 
2007-05-05 15:06:48.356 Newest Schema Version : 1160
2007-05-05 15:06:48.358 New DB connection, total: 2
2007-05-05 15:06:48.359 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:06:48.361 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-05-05 15:06:48.362 New DB connection, total: 3
2007-05-05 15:06:48.364 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:06:48.366 Told to create a NEW database schema, but the database
already has 5 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-05-05 15:06:48.367 Database Schema upgrade FAILED, unlocking.
2007-05-05 15:06:48.368 Couldn't upgrade database to new schema
2007-05-05 15:23:30.918 Using runtime prefix = /usr
2007-05-05 15:23:31.503 New DB connection, total: 1
2007-05-05 15:23:31.624 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:23:31.736 Current Schema Version: 
2007-05-05 15:23:31.833 Newest Schema Version : 1160
2007-05-05 15:23:31.929 New DB connection, total: 2
2007-05-05 15:23:31.994 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:23:32.062 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-05-05 15:23:32.066 New DB connection, total: 3
2007-05-05 15:23:32.068 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:23:32.071 Told to create a NEW database schema, but the database
already has 5 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-05-05 15:23:32.088 Database Schema upgrade FAILED, unlocking.
2007-05-05 15:23:32.090 Couldn't upgrade database to new schema
2007-05-05 15:25:29.901 Using runtime prefix = /usr
2007-05-05 15:25:29.936 New DB connection, total: 1
2007-05-05 15:25:29.941 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:25:29.944 Current Schema Version: 
2007-05-05 15:25:29.946 Newest Schema Version : 1160
2007-05-05 15:25:29.948 New DB connection, total: 2
2007-05-05 15:25:29.949 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:25:29.951 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-05-05 15:25:29.952 New DB connection, total: 3
2007-05-05 15:25:29.953 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:25:29.955 Told to create a NEW database schema, but the database
already has 5 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-05-05 15:25:29.956 Database Schema upgrade FAILED, unlocking.
2007-05-05 15:25:29.957 Couldn't upgrade database to new schema
2007-05-05 15:29:41.413 Using runtime prefix = /usr
2007-05-05 15:29:41.440 New DB connection, total: 1
2007-05-05 15:29:41.445 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:29:41.449 Current Schema Version: 
2007-05-05 15:29:41.450 Newest Schema Version : 1160
2007-05-05 15:29:41.452 New DB connection, total: 2
2007-05-05 15:29:41.454 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:29:41.455 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-05-05 15:29:41.457 New DB connection, total: 3
2007-05-05 15:29:41.458 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:29:41.460 Told to create a NEW database schema, but the database
already has 5 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-05-05 15:29:41.461 Database Schema upgrade FAILED, unlocking.
2007-05-05 15:29:41.462 Couldn't upgrade database to new schema
2007-05-05 15:36:38.373 Using runtime prefix = /usr
2007-05-05 15:36:38.401 New DB connection, total: 1
2007-05-05 15:36:38.409 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:36:38.412 Current Schema Version: 
2007-05-05 15:36:38.413 Newest Schema Version : 1160
2007-05-05 15:36:38.416 New DB connection, total: 2
2007-05-05 15:36:38.417 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:36:38.419 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-05-05 15:36:38.422 New DB connection, total: 3
2007-05-05 15:36:38.423 Connected to database 'mythconverg' at host: localhost
2007-05-05 15:36:38.426 Told to create a NEW database schema, but the database
already has 5 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-05-05 15:36:38.427 Database Schema upgrade FAILED, unlocking.
2007-05-05 15:36:38.429 Couldn't upgrade database to new schema

---

### Post by psyopper on 2007-05-05
I'm reallynew to Linux and have only dabbled in MySQL a touch under Windows but...

> Query was: CREATE TABLE IF NOT EXISTS codecparams ( profile int(10) unsigned NOT NULL default '0', name varchar(12 NOT NULL default '', value varchar(12 default NULL, PRIMARY KEY (profile,name));
Error was: Driver error was [2/2013]

This seems to be your problem. This sequence is attempting to make a table in your 'mythconverg' database on MySQL named 'codecparams'. Take a look and see if this table already exists. If it does, delete it and try the process again.

I think the code it is using in attempting to update is incorrect. I think it's missing a paranthesis, highlighted in red below:

> CREATE TABLE IF NOT EXISTS codecparams ( profile int(10) unsigned NOT NULL default '0', name varchar(12[COLOR="Red"]**)**[/COLOR] NOT NULL default '', value varchar(12[COLOR="Red"]**)**[/COLOR] default NULL, PRIMARY KEY (profile,name))

I may be wrong, but there really do seem to be some nesting issues in this statement that I need about 2 more cups of coffee to reverse engineer...

---

### Post by alwaysthenoob on 2007-05-05
Thanks for the reply,  I'll take a look, however I think those brackets in red are there, its just the forum code read them as a smiley instead of the code and made this :cool: instead.

I'll have a go anyway and post my findings

---

### Post by psyopper on 2007-05-05
Also, make sure the correct write permissions are there. I'm not sure HOW to make sure, but you could be failing because the application doesn't have the correct permissions to write to the database.

---

### Post by alwaysthenoob on 2007-05-05
ok, really showing my noobness here...how do I look in mythconverg?  is it a file or do I have to somehow log into SQL to read it...I'm in the dark here...

---

### Post by alwaysthenoob on 2007-05-05
> **psyopper said:**
> Also, make sure the correct write permissions are there. I'm not sure HOW to make sure, but you could be failing because the application doesn't have the correct permissions to write to the database.

I managed to check that part by doing : grep mythtv: /etc/group

That showed I was in the group.

Still searching for this mythconverg thinggy but cant find it as a file anywhere.

---

### Post by psyopper on 2007-05-07
It's not a file, it's a database. 

Again, I'm on new ground here, I certianly have never used MySQL on Liux. MySQL will manage the database. Open MySQL and it should be there.

---

### Post by vash5556 on 2007-05-07
you could try installing phpmyadmin which gives you a graphical view of all the databases you have in MySQL.  this would probably be the easiest way to see the permissions you have on all your databases, and should make changing permissions easy should u have to.

---

### Post by superm1 on 2007-05-07
If you are doing a fresh install, you are getting database corruption or having trouble with a schema update.  The best way to handle this:

```
sudo apt-get remove --purge mysql-server-5.0 mythtv-database
```
Drop the database when asked
```
sudo apt-get install mythtv-database mysql-server-5.0
```

There has been a few cases of this reported recently.

---

### Post by alwaysthenoob on 2007-05-08
Many thanks for the replies and help all.
I'm at work at the moment but will try out these suggestions when I get home.  I did a fresh install of feisty last night so I can try from scratch.  I'm sure the error will appear again as it has done on numerous installs but hopefully I can run those other commands and see what I get.

---

### Post by DiscMan on 2007-09-07
> **superm1 said:**
> If you are doing a fresh install, you are getting database corruption or having trouble with a schema update.  The best way to handle this:

```
sudo apt-get remove --purge mysql-server-5.0 mythtv-database
```
Drop the database when asked
```
sudo apt-get install mythtv-database mysql-server-5.0
```

There has been a few cases of this reported recently.

I had the same issue and the above steps worked for me. :)

---

