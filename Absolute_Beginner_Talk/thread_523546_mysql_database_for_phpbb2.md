---
title: "mysql database for phpbb2"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by drewsmug on 2007-08-12
i am thinking- rather hoping- that this is an easy question.

i have ubuntu and apache2 and php5 and mysql all running.
i have phpmyadmin up and have created a database.
i want phpbb to be able to use the database
all i need now is to make sure it has the right privileges.

i have options like
structure only
structure and data
data only
create database before copying
add drop table / drop view
add auto_increment value
add constraints
switch to copied database

i just know in the tutorials that dont use phpmyadmin they need to give phpbb access to use the database.  i dont know if i can just leave it like it is or if i have to change things.

i guess you should know the second and forth option came per selected.
does anybody know what i need to do
thanks in advance

---

### Post by Cypher on 2007-08-13
What I do is the following:
1. Login as Root to MySQL
2. Create a new user
3. Create a database as that new user
4. Put the credentials of the new user into the app I'm playing with and have it create it's tables.

So, that being said..start with
```

mysql -uroot

```
This will get you in as root, now do
```

mysql> GRANT ALL PRIVILEGES ON *.* TO 'testuser'@'localhost' IDENTIFIED BY 'testpass';
Query OK, 0 rows affected (0.00 sec)

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)

```

You can obviously change the username and password as you choose. Now exit from Mysql
```

mysql> exit

```
Log in as the new user
```

mysql -utestuser -p
Enter password: <testpass> goes here

```
Now you should be back into MySQL as the new user and can create the new database
```

mysql> create database foo;
Query OK, 1 row affected (0.00 sec)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| foo                |
| mysql              |
| test               |
+--------------------+
4 rows in set (0.01 sec)

```
Now in the configuration file for PHPBB2, you'd have it point to Localhost as the server, testuser as username, testpass as password, foo as the database.

---

