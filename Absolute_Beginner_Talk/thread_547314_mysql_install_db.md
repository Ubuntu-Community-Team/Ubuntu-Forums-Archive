---
title: "mysql_install_db"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by vertex78 on 2007-09-09
Hello, I am trying to learn how to use sql and after giving this command

mysql_install_db, I get this error
```

Installing MySQL system tables...
ERROR: 1062  Duplicate entry '%-test-' for key 1
070909 22:08:52 [ERROR] Aborting

070909 22:08:52 [Note] /usr/sbin/mysqld: Shutdown complete

Installation of system tables failed!

Examine the logs in /var/lib/mysql for more information.
You can try to start the mysqld daemon with:
/usr/sbin/mysqld --skip-grant &
and use the command line tool
/usr/bin/mysql to connect to the mysql
database and look at the grant tables:

shell> /usr/bin/mysql -u root mysql
mysql> show tables

Try 'mysqld --help' if you have problems with paths. Using --log
gives you a log in /var/lib/mysql that may be helpful.

The latest information about MySQL is available on the web at
http://www.mysql.com
Please consult the MySQL manual section: 'Problems running mysql_install_db',
and the manual section that describes problems on your OS.
Another information source is the MySQL email archive.
Please check all of the above before mailing us!
And if you do mail us, you MUST use the /usr/bin/mysqlbug script!

```

Any thoughts?

---

### Post by jamvegan on 2007-09-10
Perhaps it is failing because the tables are already there?  How did you install mysql?  If you used apt-get or synaptic then the tables would have been created automatically.  Is the server running (you can check this by running the following command--if there's no output, it's not running)?
```
ps -e | grep mysqld
```
Can you interact with mysql from the command line? Try the following:
```
mysql -u root 
```
If your prompt changes to the mysql prompt (mysql>), then try the following:
```
use mysql;
show tables;
```
The second command should list 15-20 tables.  If it does, then I don't think that you have any need to run mysql_install_db.  Or was there a specific reason that you need to do so?

---

### Post by tameek on 2007-09-10
Hey,

I'm trying to learn mysql as well.  When I tried the command:

ps -e | grep mysqld

I didn't get any output, just my prompt again.  Can I install mysqld from Synaptic?:confused:

---

### Post by jamvegan on 2007-09-10
> Can I install mysqld from Synaptic?

Yes, you can.  You'll want to install the mysql-server package.  Also, if you're planning to interact with it via something else, you'll want to search for appropriate packages to do that.  For instance, if you want to work with PHP and MySQL you would need to install the php5-mysql package.

---

### Post by tameek on 2007-09-10
you are correct sir.  I didn't have **mysql-server** installed.  I found it easily in Synaptic Manager.  I'm well on my way to becoming a mysql expert (not).

You rock!:guitar:

Thanks!

---

### Post by vertex78 on 2007-09-11
Ok, when I type: 
```

ps -e | grep mysqld

```
I get:
```

ps -e | grep mysqld
 4649 ?        00:00:00 mysqld_safe
 4772 ?        00:00:00 mysqld

```

When I type:
```

mysql -u root

```
I get:
```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

Then when I try:
```

mysqladmin -u root password mypass

```
```

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```

What am I doing wrong?

---

### Post by jamvegan on 2007-09-11
If you already have a root password set up for mysql, then you can log in like this:
```
mysql -u root -p
```
And you will be prompted to enter the password.

---

### Post by tameek on 2007-09-11
I get the same error when I try to login with a username that doesn't exits

(for example)

**#mysql -u tameek**

I get the same error:

**ERROR 1045 (28000): Access denied for user 'tameek'@'localhost' (using password: NO)**

...sounds like a possible botched install of MYSQL.:confused:  Could you possible reinstall MySQL.? I used Synaptic Package Manager and it installed flawless.  Get a second opinion first before taking my advice.

Good Luck

---

