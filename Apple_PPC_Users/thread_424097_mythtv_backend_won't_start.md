---
title: "mythtv backend won't start"
date: 2007-04-26
forum: Apple PPC Users
---

### Post by snown on 2007-04-26
I'm not sure if I'm posting this in the right place, but I have a old Yikes! G4 tower that I've installed Ubuntu on, and now MythTV. the problem is that the mythbackend won't start or launch. Here's a log of the happenings:

```

$ more /var/log/mythtv/mythbackend.log

2007-04-26 00:49:28.081 Using runtime prefix = /usr
QSettings: error creating /root/.qt
QSettings::sync: filename is null/empty
2007-04-26 00:49:28.609 New DB connection, total: 1
2007-04-26 00:49:28.630 Unable to connect to database!
2007-04-26 00:49:28.644 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-04-26 00:49:28.717 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-04-26 00:49:28.784 Failed to init MythContext, exiting.
```

---

### Post by msak007 on 2007-04-30
I assume you're using Feisty? If you are, try this page:

[https://help.ubuntu.com/community/MythTV/Install/Feisty/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Feisty/Troubleshooting)

Here's the main page with all the MythTV how-tos

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

