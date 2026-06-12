---
title: "mysql and ubuntu?"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by gleble on 2007-12-16
When I used to create databases in windows I would get the mysql editing window up and I could make databasess on my local server. How do I create databases in ubuntu. I have apache2 and php5 installed

---

### Post by HermanAB on 2007-12-16
Try phpmyadmin.  It should be in Synaptic.

Cheers,

Herman

---

### Post by LaRoza on 2007-12-16
> **gleble said:**
> When I used to create databases in windows I would get the mysql editing window up and I could make databasess on my local server. How do I create databases in ubuntu. I have apache2 and php5 installed

Do you have MySQL?

To install LAMPP, ```
sudo tasksel
```

I use MySQL through the command line usually:

```

mysql -u root -p

```

---

### Post by gleble on 2007-12-16
I do have mysql, my problem is how to access it.

---

### Post by LaRoza on 2007-12-16
> **gleble said:**
> I do have mysql, my problem is how to access it.
```

mysql -u root -p

```

---

### Post by gleble on 2007-12-17
OK put in mysql -u root -p One of my problems was that I didn't know my username so I made some up and I get to
```
mysql  Ver 14.12 Distrib 5.0.45, for pc-linux-gnu (i486) using readline 5.2
Copyright (C) 2002 MySQL AB
``` and a load of info
so I presume I'm there. However when I enter simple commands such as show and create it tells me they are not available. Where am I going wrong?

---

### Post by jflaker on 2007-12-17
you can get phpmyadmin......look for it in Synaptic.  Once installed, you can access it from your browser at [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

it doesn't give you everything that the MySQL GUI gives you, but it is a very functional web app.

good luck.

---

### Post by gleble on 2007-12-17
Got phpmyadmin but when I go to http;//localhost/phpadmin I get

```
Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.
```

I'd still like to get to the Mysql GUI

---

### Post by hyper_ch on 2007-12-17
post the output of:

```

ls -al /var/www

```

---

### Post by jflaker on 2007-12-17
> **gleble said:**
> Got phpmyadmin but when I go to http;//localhost/phpadmin I get

```
Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.
```

I'd still like to get to the Mysql GUI

Try [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

---

### Post by gleble on 2007-12-17
```
neil@neil-laptop:~$ ls -al /var/www
total 92
drwxr-xr-x  3 root root  4096 2007-12-14 20:34 .
drwxr-xr-x 16 root root  4096 2007-12-05 20:39 ..
-rw-r--r--  1 neil neil  5215 2007-12-09 17:49 airport36hr.htm
drwxr-xr-x  2 root root  4096 2007-12-05 20:39 apache2-default
-rw-r--r--  1 root root   897 2007-10-14 21:10 favicon.ico
-rw-r--r--  1 root root  5018 2007-12-11 19:20 first.htm
-rw-r--r--  1 root root  5017 2007-12-11 19:18 first.htm~
-rw-r--r--  1 neil neil  1519 2007-12-02 17:10 headandnavs.inc
-rw-r--r--  1 root root 13428 2007-10-16 20:00 logo.gif
-rw-r--r--  1 neil neil  1936 2007-12-10 19:05 minutes.php
lrwxrwxrwx  1 root root    17 2007-12-11 18:25 neil -> /home/heil/Public
-rw-r--r--  1 root root  1503 2007-12-02 17:11 sidebar.inc
-rw-r--r--  1 root root  1947 2007-11-28 11:21 solar.php
-rw-r--r--  1 root root  4490 2007-11-08 18:50 ueceg2.css
-rw-r--r--  1 root root  1235 2007-10-14 21:20 ueceg2.php
-rw-r--r--  1 root root  4555 2007-11-08 18:57 ueceg.css
```
Any help?

---

### Post by hyper_ch on 2007-12-17
do you have files in:  /etc/apache2/conf.d ?

---

### Post by gleble on 2007-12-17
'charset' and' phpmyadmin.conf' which is linked to '/etc/phpmyadmin/apache.conf'

---

### Post by hyper_ch on 2007-12-17
then you should be able to accerss it by  [http://localhost/phpmyadmin](http://localhost/phpmyadmin)  or  [http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin)

---

### Post by jflaker on 2007-12-17
maybe the apache server isn't started?  only thing I can think of.....

Not sure of the command to start apache.

---

### Post by gleble on 2007-12-17
see posting #8 in this thread
apache is running, I can access [http://localhost/index.php](http://localhost/index.php) for instance

---

### Post by njparton on 2007-12-17
```
/etc/init.d/apache start
```
or
```
/etc/init.d/apache2 start
```

---

### Post by gleble on 2007-12-17
see #16

---

### Post by svalding on 2007-12-17
I use MySQL Administrator available through synaptic. It's a great little GUI application for administering MySQL that allows you to do user administration, database administration, server administration, and backup functions. Wonderful little tool.

---

### Post by gleble on 2007-12-17
what do you put in synaptic.? I can't find it.

---

### Post by jflaker on 2007-12-17
do a search for "mysql' (no quotes).......down the page under MySQL, you should find the administrator and other tools

---

### Post by gleble on 2007-12-17
OK got here
```
mysql  Ver 14.12 Distrib 5.0.45, for pc-linux-gnu (i486) using readline 5.2
Copyright (C) 2002 MySQL AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license
Usage: mysql [OPTIONS] [database]
  -?, --help          Display this help and exit.
  -I, --help          Synonym for -?
  --auto-rehash       Enable automatic rehashing. One doesn't need to use
                      'rehash' to get table and field completion, but startup
                      and reconnecting may take a longer time. Disable with
                      --disable-auto-rehash.
  -A, --no-auto-rehash 
                      No automatic rehashing. One has to use 'rehash' to get
                      table and field completion. This gives a quicker start of
                      mysql and disables rehashing on reconnect. WARNING:
                      options deprecated; use --disable-auto-rehash instead.
  -B, --batch         Don't use history file. Disable interactive behavior.
                      (Enables --silent)
  --character-sets-dir=name 
                      Directory where character sets are.
  --default-character-set=name 
```
a llong list follows, How do I enter these commands?
Nothing seems to work

---

### Post by KCPokes on 2007-12-17
There are a couple other, perhaps older, threads out there regarding the same concerns.  I typically use phpMyAdmin or Webmin (which will give you the basics), there is a program called DBDesigner that looks promising.  I've heard there are some challenges with getting it installed, but might be worth the work.  I keep forgetting to mess with it until I see threads like this.  

[http://ubuntuforums.org/showthread.php?t=604936](http://ubuntuforums.org/showthread.php?t=604936)  ... a thread with the same questions (GUI frontend for MySQL).

---

### Post by gleble on 2007-12-17
I can't access phpmyadmin , see above. I've got something called MySQL Administrator up. What do I enter for Server hostname?. I've tried 127.0.0.1 and it doesn't like it

---

### Post by gleble on 2007-12-17
I've got MySQL Query browser now but same problems don't know what to enter

---

### Post by Winterdream on 2007-12-17
This tutorial:
[http://dev.mysql.com/doc/refman/5.0/en/tutorial.html](http://dev.mysql.com/doc/refman/5.0/en/tutorial.html)
should answer your questions about what to enter at the MySQL prompt.

---

### Post by gleble on 2007-12-17
I'mm afraid it doesn't help at all . I can get in  using ```
shell> mysql -h host -u user -p
```
or even
```
shell> mysql -u user -p
```
-h is simply root and I can't put that in. In fact the only thing that pings is 127.0.0.1 so I,m lost again

---

### Post by Winterdream on 2007-12-17
> **gleble said:**
> I'mm afraid it doesn't help at all . I can get in  using ```
shell> mysql -h host -u user -p
```
or even
```
shell> mysql -u user -p
```


So you are getting to the mysql prompt?  If so, what do you want to do?  Do you want to create a new database or do you want to look at the existing databases or what??  I don't understand what you're trying to do...

---

### Post by gleble on 2007-12-17
I'm in terminal and having got that far cannot enter create or show or anything I understand.

---

### Post by Winterdream on 2007-12-17
> **gleble said:**
> I'm in terminal and having got that far cannot enter create or show or anything I understand.

OK, I understand.  I just went through all this a few days ago, so I'll do it again and give you the exact steps.  I'll post it all in just a minute.

---

### Post by The Cog on 2007-12-17
if **mysql -h host -u user -p** works, the server name you put into mysql-admin or mysql-query-browser is **host**. This really shouldn't be a problem - they GUI connection dialogs take the same arguments as the text-mode mysql client.

---

### Post by Winterdream on 2007-12-17
There's three steps:
1.  Login to the mysql command line
2.  Create a user and grant privileges
3.  Create a database

Go to Applications -> Accessories -> Terminal
At the prompt, enter this:
```
mysql -u root -p
```
Then enter your root password, you have to be root to proceed.

Now you should be looking at the mysql monitor prompt:
```
mysql>
```
So you can create a user and grant privileges:
```
mysql> GRANT ALL ON testbase.* TO 'myuser'@'localhost' IDENTIFIED BY 'mypswd';
```
The database name is "testbase", the username is "myuser" and the password is "mypswd".
MySQL will print this:  "Query OK, 0 rows affected (0.00 sec)"

No you can quit (just enter QUIT) and then login as the user you've created.
```
mysql> quit
Bye
myname@myname-ubuntu:~$

```

Login as the user:
```
myname@myname-ubuntu:~$ mysql -h localhost -p -u myuser
Enter password:

```
Use the password you created above "mypswd".  Now you've got the mysql monitor prompt again (mysql>)
Next you have to create the database (you've only granted privileges to it, it doesn't really exist yet).
```
mysql> CREATE DATABASE testbase;
Query OK, 1 row affected (0.00 sec)

```
Then use database:
```
mysql> USE testbase;
Database changed

```
Then show databases:
```
mysql> SHOW DATABASES;
```

Then read the tutorial!

Let me know where you get stuck, if you can't follow this.

---

### Post by gleble on 2007-12-17
I never get to mysql>   it's always neil@neil-laptop:~$ 
```
neil@neil-laptop:~$ mysql gleb host souhami
mysql  Ver 14.12 Distrib 5.0.45, for pc-linux-gnu (i486) using readline 5.2
Copyright (C) 2002 MySQL AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license
Usage: mysql [OPTIONS] [database]
  -?, --help          Display this help and exit.
  -I, --help          Synonym for -?
  --auto-rehash       Enable automatic rehashing. One doesn't need to use
                      'rehash' to get table and field completion, but startup
                      and reconnecting may take a longer time. Disable with
                      --disable-auto-rehash.
  -A, --no-auto-rehash 
                      No automatic rehashing. One has to use 'rehash' to get
                      table and field completion. This gives a quicker start of
                      mysql and disables rehashing on reconnect. WARNING:
                      options deprecated; use --disable-auto-rehash instead.
  -B, --batch         Don't use history file. Disable interactive behavior.
                      (Enables --silent)
  --character-sets-dir=name 
                      Directory where character sets are.
  --default-character-set=name 
                      Set the default character set.
  -C, --compress      Use compression in server/client protocol.
  -#, --debug[=#]     This is a non-debug version. Catch this and exit
  -D, --database=name Database to use.
  --delimiter=name    Delimiter to be used.
  -e, --execute=name  Execute command and quit. (Disables --force and history
                      file)
  -E, --vertical      Print the output of a query (rows) vertically.
  -f, --force         Continue even if we get an sql error.
  -G, --named-commands 
                      Enable named commands. Named commands mean this program's
                      internal commands; see mysql> help . When enabled, the
                      named commands can be used from any line of the query,
                      otherwise only from the first line, before an enter.
                      Disable with --disable-named-commands. This option is
                      disabled by default.
  -g, --no-named-commands 
                      Named commands are disabled. Use \* form only, or use
                      named commands only in the beginning of a line ending
                      with a semicolon (;) Since version 10.9 the client now
                      starts with this option ENABLED by default! Disable with
                      '-G'. Long format commands still work from the first
                      line. WARNING: option deprecated; use
                      --disable-named-commands instead.
  -i, --ignore-spaces Ignore space after function names.
  --local-infile      Enable/disable LOAD DATA LOCAL INFILE.
  -b, --no-beep       Turn off beep on error.
  -h, --host=name     Connect to host.
  -H, --html          Produce HTML output.
  -X, --xml           Produce XML output
  --line-numbers      Write line numbers for errors.
  -L, --skip-line-numbers 
                      Don't write line number for errors. WARNING: -L is
                      deprecated, use long version of this option instead.
  -n, --unbuffered    Flush buffer after each query.
  --column-names      Write column names in results.
  -N, --skip-column-names 
                      Don't write column names in results. WARNING: -N is
                      deprecated, use long version of this options instead.
  -O, --set-variable=name 
                      Change the value of a variable. Please note that this
                      option is deprecated; you can set variables directly with
                      --variable-name=value.
  --sigint-ignore     Ignore SIGINT (CTRL-C)
  -o, --one-database  Only update the default database. This is useful for
                      skipping updates to other database in the update log.
  --pager[=name]      Pager to use to display results. If you don't supply an
                      option the default pager is taken from your ENV variable
                      PAGER. Valid pagers are less, more, cat [> filename],
                      etc. See interactive help (\h) also. This option does not
                      work in batch mode. Disable with --disable-pager. This
                      option is disabled by default.
  --no-pager          Disable pager and print to stdout. See interactive help
                      (\h) also. WARNING: option deprecated; use
                      --disable-pager instead.
  -p, --password[=name] 
                      Password to use when connecting to server. If password is
                      not given it's asked from the tty. WARNING: This is
                      insecure as the password is visible for anyone through
                      /proc for a short time.
  -P, --port=#        Port number to use for connection.
  --prompt=name       Set the mysql prompt to this value.
  --protocol=name     The protocol of connection (tcp,socket,pipe,memory).
  -q, --quick         Don't cache result, print it row by row. This may slow
                      down the server if the output is suspended. Doesn't use
                      history file.
  -r, --raw           Write fields without conversion. Used with --batch.
  --reconnect         Reconnect if the connection is lost. Disable with
                      --disable-reconnect. This option is enabled by default.
  -s, --silent        Be more silent. Print results with a tab as separator,
                      each row on new line.
  -S, --socket=name   Socket file to use for connection.
  --ssl               Enable SSL for connection (automatically enabled with
                      other flags). Disable with --skip-ssl.
  --ssl-ca=name       CA file in PEM format (check OpenSSL docs, implies
                      --ssl).
  --ssl-capath=name   CA directory (check OpenSSL docs, implies --ssl).
  --ssl-cert=name     X509 cert in PEM format (implies --ssl).
  --ssl-cipher=name   SSL cipher to use (implies --ssl).
  --ssl-key=name      X509 key in PEM format (implies --ssl).
  --ssl-verify-server-cert 
                      Verify server's "Common Name" in its cert against
                      hostname used when connecting. This option is disabled by
                      default.
  -t, --table         Output in table format.
  -T, --debug-info    Print some debug info at exit.
  --tee=name          Append everything into outfile. See interactive help (\h)
                      also. Does not work in batch mode. Disable with
                      --disable-tee. This option is disabled by default.
  --no-tee            Disable outfile. See interactive help (\h) also. WARNING:
                      option deprecated; use --disable-tee instead
  -u, --user=name     User for login if not current user.
  -U, --safe-updates  Only allow UPDATE and DELETE that uses keys.
  -U, --i-am-a-dummy  Synonym for option --safe-updates, -U.
  -v, --verbose       Write more. (-v -v -v gives the table output format).
  -V, --version       Output version information and exit.
  -w, --wait          Wait and retry if connection is down.
  --connect_timeout=# Number of seconds before connection timeout.
  --max_allowed_packet=# 
                      Max packet length to send to, or receive from server
  --net_buffer_length=# 
                      Buffer for TCP/IP and socket communication
  --select_limit=#    Automatic limit for SELECT when using --safe-updates
  --max_join_size=#   Automatic limit for rows in a join when using
                      --safe-updates
  --secure-auth       Refuse client connecting to server if it uses old
                      (pre-4.1.1) protocol
  --show-warnings     Show warnings after every statement.

Default options are read from the following files in the given order:
/etc/mysql/my.cnf ~/.my.cnf /usr/etc/my.cnf 
The following groups are read: mysql client
The following options may be given as the first argument:
--print-defaults        Print the program argument list and exit
--no-defaults           Don't read default options from any options file
--defaults-file=#       Only read default options from the given file #
--defaults-extra-file=# Read this file after the global files are read

Variables (--variable-name=value)
and boolean options {FALSE|TRUE}  Value (after reading options)
--------------------------------- -----------------------------
auto-rehash                       TRUE
character-sets-dir                (No default value)
default-character-set             latin1
compress                          FALSE
database                          (No default value)
delimiter                         ;
vertical                          FALSE
force                             FALSE
named-commands                    FALSE
local-infile                      FALSE
no-beep                           FALSE
host                              (No default value)
html                              FALSE
xml                               FALSE
line-numbers                      TRUE
unbuffered                        FALSE
column-names                      TRUE
sigint-ignore                     FALSE
port                              3306
prompt                            mysql> 
quick                             FALSE
raw                               FALSE
reconnect                         TRUE
socket                            /var/run/mysqld/mysqld.sock
ssl                               FALSE
ssl-ca                            (No default value)
ssl-capath                        (No default value)
ssl-cert                          (No default value)
ssl-cipher                        (No default value)
ssl-key                           (No default value)
ssl-verify-server-cert            FALSE
table                             FALSE
debug-info                        FALSE
user                              (No default value)
safe-updates                      FALSE
i-am-a-dummy                      FALSE
connect_timeout                   0
max_allowed_packet                16777216
net_buffer_length                 16384
select_limit                      1000
max_join_size                     1000000
secure-auth                       FALSE
show-warnings                     FALSE
neil@neil-laptop:~$ 
```

---

### Post by KCPokes on 2007-12-17
You need to make sure you are using the flags (i.e -u, -h, -p, etc...).  Otherwise mysql doesn't understand what you are passing it.

---

### Post by gleble on 2007-12-17
OK I never understood flags, but
```
neil@neil-laptop:~$ mysql -u gleb -h localhost -p pigpen;
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
neil@neil-laptop:~
```$ 
Not out the woods yet, no folder /var/run/mysqld ?

---

### Post by KCPokes on 2007-12-17
Doesn't look like mysql is running on your machine, hence the error.  Can you do a "ps -ef | grep mysql" and verify that you indeed have it running?

---

### Post by gleble on 2007-12-17
```
neil@neil-laptop:~$ ps -ef | grep mysql
neil      5740     1  0 15:51 ?        00:00:00 /bin/sh /usr/bin/firefox http://www.sitepoint.com/books/Kevs-php-mysql.pdf
neil      5753  5740  0 15:51 ?        00:00:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bin http://www.sitepoint.com/books/Kevs-php-mysql.pdf
neil      5757  5753 27 15:51 ?        01:22:54 /usr/lib/firefox/firefox-bin http://www.sitepoint.com/books/Kevs-php-mysql.pdf
neil      7139  7121  0 20:48 pts/0    00:00:00 grep mysql
neil@neil-laptop:~$ 
```
Doesn't look like it is, how do I start it?

---

### Post by KCPokes on 2007-12-17
```

sudo /etc/init.d/mysql start

```

That should start it for you.

---

### Post by gleble on 2007-12-17
No mysql in init.d

---

### Post by KCPokes on 2007-12-17
Are you sure that you have MySql installed?  I run it locally, on my laptop, for development purposes, so I did verify that you should have mysql in your /etc/init.d directory.  It is not installed by default, thus unless you built it from source, I'd expect to see it in the /etc/init.d directory.

---

### Post by gleble on 2007-12-17
In at long last, thanks to all of you
```
neil@neil-laptop:~$ mysql -u root -h localhost -p ;
Enter password: 
```
did it

---

### Post by The Cog on 2007-12-18
Excellent.

It is definitely worth installing some kind of a GUI program for MySQL though.I use mysql-admin and mysql-query-browser.

---

### Post by gleble on 2007-12-18
Cheers got both of them but I'm getting on with the monitor best.

---

