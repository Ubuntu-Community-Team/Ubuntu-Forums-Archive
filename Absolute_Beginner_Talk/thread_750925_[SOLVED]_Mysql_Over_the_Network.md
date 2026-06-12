---
title: "[SOLVED] Mysql Over the Network"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by The Titan on 2008-04-10
I have 2 computers on a network, 192.168.0.2 is my server and 192.168.0.3 is my workstation.  My problem is that when i try to connect to MySQL from Zend i get a "Ping Failed" error.

her is my "my.cnf" file:
```

root@temple:/etc/mysql# cat my.cnf
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
#
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0

[mysqld]
#
# * Basic Settings
#
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
language        = /usr/share/mysql/english
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 192.168.0.2
#
# * Fine Tuning
#
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 128K
thread_cache_size       = 8
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log            = /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
#
# Here you can see queries with especially long duration
#log_slow_queries       = /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id              = 1
log_bin                 = /var/log/mysql/mysql-bin.log
# WARNING: Using expire_logs_days without bin_log crashes the server! See README.Debian!
expire_logs_days        = 10
max_binlog_size         = 100M
#binlog_do_db           = include_database_name
#binlog_ignore_db       = include_database_name
#
# * BerkeleyDB
#
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet      = 16M

[mysql]
#no-auto-rehash # faster start of mysql but no tab completition

[isamchk]
key_buffer              = 16M

#
# * NDB Cluster
#
# See /usr/share/doc/mysql-server-*/README.Debian for more information.
#
# The following configuration is read by the NDB Data Nodes (ndbd processes)
# not from the NDB Management Nodes (ndb_mgmd processes).
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1


#
# * IMPORTANT: Additional settings that can override those from this file!
#
!includedir /etc/mysql/conf.d/

root@temple:/etc/mysql#         

```

If you need any other information please let me know.   It is ubuntu server 7.10.

---

### Post by tamoneya on 2008-04-10
change ```
bind-address            = 192.168.0.2

``` to ```
#bind-address            = 192.168.0.2

``` and then restart the mysql server.  What happens why you just type ```
ping 192.168.0.2
``` into terminal

---

### Post by The Titan on 2008-04-10
> **tamoneya said:**
> change ```
bind-address            = 192.168.0.2

``` to ```
#bind-address            = 192.168.0.2

``` and then restart the mysql server.  What happens why you just type ```
ping 192.168.0.2
``` into terminal
No dice =/   I can ping it fine from the terminal, but this is interesting look at this

The Address im using:
```

jdbc:mysql://192.168.0.2:3306

```

The error i get:
```

java.sql.SQLException: Access denied for user [COLOR=Red]'root'@'192.168.0.3' (using password: NO)[/COLOR]
    at com.mysql.jdbc.SQLError.createSQLException(SQLError.java:946)
    at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:2985)
    at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:885)
    at com.mysql.jdbc.MysqlIO.secureAuth411(MysqlIO.java:3421)
    at com.mysql.jdbc.MysqlIO.doHandshake(MysqlIO.java:1247)
    at com.mysql.jdbc.Connection.createNewIO(Connection.java:2748)
    at com.mysql.jdbc.Connection.<init>(Connection.java:1553)
    at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:285)
    at com.zend.php.datatools.core.connection.JDBCConnection.createConnection(Unknown Source)
    at org.eclipse.datatools.connectivity.DriverConnectionBase.internalCreateConnection(DriverConnectionBase.java:104)
    at org.eclipse.datatools.connectivity.DriverConnectionBase.open(DriverConnectionBase.java:53)
    at com.zend.php.datatools.core.connection.JDBCConnectionFactory.createConnection(Unknown Source)
    at org.eclipse.datatools.connectivity.internal.ConnectionFactoryProvider.createConnection(ConnectionFactoryProvider.java:77)
    at org.eclipse.datatools.connectivity.internal.ConnectionProfile.createConnection(ConnectionProfile.java:354)
    at org.eclipse.datatools.connectivity.ui.PingJob.run(PingJob.java:57)
    at org.eclipse.core.internal.jobs.Worker.run(Worker.java:55)

```

Is it just me or is there something else wrong there?

---

### Post by tamoneya on 2008-04-10
it doesnt look like a ping problem to me.  It seems like it sees the server but you just gave it the wrong password.

---

### Post by The Titan on 2008-04-10
> **tamoneya said:**
> it doesnt look like a ping problem to me.  It seems like it sees the server but you just gave it the wrong password.
no i was just experimenting and didn't put one in that time.  I have tried it with the right password, and different accounts.

---

### Post by gerscht on 2008-04-10
Sorry, didn't read the last one.
Heres what I wrote, which might be obsolete:
-
you can't connect to a mysql server without password if the server is not 'localhost'.
set a password and it should be fine.

---

### Post by The Titan on 2008-04-10
> **gerscht said:**
> Sorry, didn't read the last one.
Heres what I wrote, which might be obsolete:
-
you can't connect to a mysql server without password if the server is not 'localhost'.
set a password and it should be fine.
I just dont get why it says access denied at "192.168.0.3".  I"m trying to connect to 192.168.0.2 and that is what is in the address.

---

### Post by apostate on 2008-04-11
> **The Titan said:**
> I just dont get why it says access denied at "192.168.0.3".  I"m trying to connect to 192.168.0.2 and that is what is in the address.

But are you coming *from* 192.168.0.3?

For security, MySQL will not accept connections (even from a valid user with password) that come from a different machine, unless the account was set up to be eligible to connect from multiple hosts. This is a MySQL issue. 

For instance:

GRANT ALL ON mydb.* TO 'someuser'@'localhost';

Means that someuser can ONLY connect locally, not from another machine, even if the right password is given.  But if you do:

GRANT ALL ON mydb.* TO 'someuser'@'%';

It will work.  Maybe this will help.

---

### Post by hyper_ch on 2008-04-11
or use phpMyAdmin to alter the users in a convenient way...

---

### Post by The Titan on 2008-04-11
> **apostate said:**
> But are you coming *from* 192.168.0.3?

For security, MySQL will not accept connections (even from a valid user with password) that come from a different machine, unless the account was set up to be eligible to connect from multiple hosts. This is a MySQL issue. 

For instance:

GRANT ALL ON mydb.* TO 'someuser'@'localhost';

Means that someuser can ONLY connect locally, not from another machine, even if the right password is given.  But if you do:

GRANT ALL ON mydb.* TO 'someuser'@'%';

It will work.  Maybe this will help.
batta bing batta boom! Worked, Thank you!

---

### Post by apostate on 2008-04-11
> **The Titan said:**
> batta bing batta boom! Worked, Thank you!

My pleasure.

---

