---
title: "Set Root Password for Install MySQL in Mac Air"
date: 2011-04-08
forum: Apple Hardware Users
---

### Post by yteng on 2011-04-08
bash-3.2$ /usr/local/mysql/bin/mysql -u root mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.5.11-log MySQL Community Server (GPL)

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>

mysql> SELECT User, Host, Password FROM mysql.user;
+------+-------------------------------+----------+
| User | Host                          | Password |
+------+-------------------------------+----------+
| root | localhost                     |          |
| root | t61.corp.mycorp.com |          |
| root | 127.0.0.1                     |          |
| root | ::1                           |          |
|      | localhost                     |          |
|      | t61.corp.mycorp.com |          |
+------+-------------------------------+----------+
6 rows in set (0.00 sec)

mysql> UPDATE mysql.user SET Password = PASSWORD('yteng')   WHERE User = 'root';
Query OK, 4 rows affected (0.00 sec)
Rows matched: 4  Changed: 4  Warnings: 0

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)

mysql> SELECT User, Host, Password FROM mysql.user;
+------+-------------------------------+-------------------------------------------+
| User | Host                          | Password                                  |
+------+-------------------------------+-------------------------------------------+
| root | localhost                     | *5D444D358D630D2FE1C3B69DBBCF50AAB3A1BAD1 |
| root | t61.corp.fmycorp.com | *5D444D358D630D2FE1C3B69DBBCF50AAB3A1BAD1 |
| root | 127.0.0.1                     | *5D444D358D630D2FE1C3B69DBBCF50AAB3A1BAD1 |

---

