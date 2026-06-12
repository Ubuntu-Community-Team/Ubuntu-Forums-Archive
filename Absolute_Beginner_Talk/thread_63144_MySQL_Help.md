---
title: "MySQL Help"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by zero17 on 2005-09-07
I have a back up file from MySQL database, and the file name is hierm.sql.

and I want to put back or read back into the database, I've tried using:

```
adit@ubuntu:/var/www/hierm$ mysql hierm < hierm.sql
ERROR 1044: Access denied for user: '@localhost' to database 'hierm'

```

do you guys have any idea, why?

even though when I tried to use sudo

```
adit@ubuntu:/var/www/hierm$ sudo mysql hierm < hierm.sql
ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)
```

any suggestion...?????

---

### Post by kirsche on 2005-09-07
try connecting to the mysql with a password for root, e.g.
mysql -u root -p

---

