---
title: "Sudoers File, allowing 'chown -R anotheruser:staff'"
date: 2012-03-06
forum: Apple Hardware Users
---

### Post by hateborne on 2012-03-06
Afternoon Ladies and Gents,

I am trying to allow a user to change the ownership of a folder to another user. We have a generic account with a disgustingly overkill password (that is never logged in), that is used only for running cron tasks and other generic tasks that do NOT require root access. However, we recently moved two tasks over from the root crontab. One was a 'killall' task, which works. The other is a small, over-simplistic database backup. The last line of the backup script is 'chown -R dbuser:staff /User/dbuser/dbbackup'. 

Bit from sudoers file:
```
systasks        ALL= NOPASSWD: /usr/bin/killall, /bin/cp -[rp] /Users/sysadmin/db /Users/dbuser/dbbackup, /usr/sbin/chown -[R] dbuser\:staff /Users/dbuser/dbbackup/
```Script:
```

#!/bin/bash

DB="db"
DIR="/Users/dbuser"
UG="dbuser:staff"

rm -rf "$DIR/$DB"
cp -rp "$DB" "$DIR/$DB"
chown -R $UG "$DIR/$DB"

```The user with has this task as a cron: **systasks**
The user that owns (and will own) the backups: **dbuser**
The original owner of the DB folder: **sysadmin**

This is happening on 10.6.8 Server.

Thank You!
-Hate

---

### Post by hateborne on 2012-03-07
Ok, removed the **systask** account. Everything that **systask** was supposed to do, is now being done by **dbuser**.

Excerpt from sudoers:
```
systasks        ALL= NOPASSWD: /usr/bin/killall, /bin/cp
```


Thanks!

-Hate

---

