---
title: "Error using mysqladmin"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Streetwalker32 on 2006-10-20
I cannot use the mysql command.
I get the error:
Access denied for user 'root'@'localhost' (using password: YES)

The same error when trying:
sudo mysqladmin ping
sudo mysqladmin ping -p[newrootsqlpassword]
sudo mysqladmin create

---

### Post by dbd on 2006-10-20
This should help:
[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

---

### Post by clarkth on 2006-10-20
I had the same problem.  I had to log into sql with the root and no password then update the mysql.user table password for the root user diretly.

---

### Post by Abhi Kalyan on 2006-11-04
learning

---

