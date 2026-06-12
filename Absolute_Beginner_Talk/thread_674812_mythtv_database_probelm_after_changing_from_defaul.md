---
title: "mythtv database probelm after changing from default user"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2008-01-22
I have installed mythtv and it was running fine. untill i changed the default "mythtv" user to myself...now, instead of booting to the mythtv page, i get a weird version of my desktop in a mythbuntu theme. when i run in a terminal ```
mythtv
``` i get the error ```
No error type from QSqlError?  Strange...
2008-01-22 20:12:57.978 Unable to connect to database!
2008-01-22 20:12:57.979 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: NO)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-22 20:12:58.071 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-22 20:12:58.121 Failed to init MythContext, exiting.

```
then it takes me to the database config page...so it would seem by changing from the default mythtv user to myself, the database has gone weird?

---

### Post by jd65pl on 2008-01-22
Have you granted yourself rights for the database? I don't think the database has gone weird you just haven't got access to it.

If your not familiar with structuring mysql queries and mysql admin then I suggest you install apache, php5 and phpmyadmin. You can then use phpmyadmin to configure your database and change permissions.

Post back if you need more help!

---

### Post by e1ektrob0y on 2008-01-22
hmmm, well i just removed the mythtv frontend, so now i think the best thing to do would be start form scratch...

---

