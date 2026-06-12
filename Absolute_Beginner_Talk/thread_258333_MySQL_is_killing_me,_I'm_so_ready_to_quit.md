---
title: "MySQL is killing me, I'm so ready to quit"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by locoHost on 2006-09-15
How many days should spend trying to get MySQL (which worked Ok about a month ago) running? I'm Googling and Googling and Googling and searching forum after forum after forum. I find lots of info and terminal commands that claim they will fix my error.Nothing ever does.

In terminal I type: mysql

I get...

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I've been reading posts and trying stuff for days. I'm at the end of my rope. Seriously guys, what is going on?

---

### Post by ruedu on 2006-09-15
MySQL is not running at all.  On the command line you can sudo /etc/init.d/mysql start  

That should start it and alert you to any errors that might be causing it to not start.

---

### Post by locoHost on 2006-09-15
mark@d6games:~$ sudo /etc/init.d/mysql start
Password:
Starting MySQL database server: mysqld.
.
.
.
.
.
.
.
.
.
.
.
.
.
...failed or took more than 6s.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

---

### Post by locoHost on 2006-09-15
Sep 15 19:57:21 localhost mysqld[16641]: InnoDB: Unable to lock ./ibdata1, error: 11
Sep 15 19:57:21 localhost mysqld[16641]: InnoDB: Check that you do not already have another mysqld process
Sep 15 19:57:21 localhost mysqld[16641]: InnoDB: using the same InnoDB data or log files.
Sep 15 19:57:22 localhost mysqld[16641]: InnoDB: Unable to lock ./ibdata1, error: 11
Sep 15 19:57:22 localhost mysqld[16641]: InnoDB: Check that you do not already have another mysqld process
Sep 15 19:57:22 localhost mysqld[16641]: InnoDB: using the same InnoDB data or log files.
Sep 15 19:57:23 localhost mysqld[16641]: InnoDB: Unable to lock ./ibdata1, error: 11
Sep 15 19:57:23 localhost mysqld[16641]: InnoDB: Check that you do not already have another mysqld process
Sep 15 19:57:23 localhost mysqld[16641]: InnoDB: using the same InnoDB data or log files.
Sep 15 19:57:24 localhost mysqld[16641]: InnoDB: Unable to lock ./ibdata1, error: 11
Sep 15 19:57:24 localhost mysqld[16641]: InnoDB: Check that you do not already have another mysqld process
Sep 15 19:57:24 localhost mysqld[16641]: InnoDB: using the same InnoDB data or log files.
Sep 15 19:57:24 localhost mysqld[16641]: 060915 19:57:24  InnoDB: Unable to open the first data file
Sep 15 19:57:24 localhost mysqld[16641]: InnoDB: Error in opening ./ibdata1
Sep 15 19:57:24 localhost mysqld[16641]: 060915 19:57:24  InnoDB: Operating system error number 11 in a file operation.
Sep 15 19:57:24 localhost mysqld[16641]: InnoDB: Error number 11 means 'Resource temporarily unavailable'.
Sep 15 19:57:24 localhost mysqld[16641]: InnoDB: Some operating system error numbers are described at
Sep 15 19:57:24 localhost mysqld[16641]: InnoDB: [http://dev.mysql.com/doc/mysql/en/Operating_System_error_codes.html](http://dev.mysql.com/doc/mysql/en/Operating_System_error_codes.html)
Sep 15 19:57:24 localhost mysqld[16641]: InnoDB: Could not open or create data files.
Sep 15 19:57:24 localhost mysqld[16641]: InnoDB: If you tried to add new data files, and it failed here,
Sep 15 19:57:24 localhost mysqld[16641]: InnoDB: you should now edit innodb_data_file_path in my.cnf back
Sep 15 19:57:24 localhost mysqld[16641]: InnoDB: to what it was, and remove the new ibdata files InnoDB created
Sep 15 19:57:24 localhost mysqld[16641]: InnoDB: in this failed attempt. InnoDB only wrote those files full of
Sep 15 19:57:24 localhost mysqld[16641]: InnoDB: zeros, but did not yet use them in any way. But be careful: do not
Sep 15 19:57:24 localhost mysqld[16641]: InnoDB: remove old data files which contain your precious data!
Sep 15 19:57:24 localhost mysqld[16641]: 060915 19:57:24 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Sep 15 19:57:24 localhost mysqld[16641]: 060915 19:57:24 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Sep 15 19:57:24 localhost mysqld[16641]: 060915 19:57:24 [ERROR] Aborting

---

### Post by locoHost on 2006-09-15
there is no other "mysqld" process running. No mysql process of any kind is running.

---

### Post by sultanoswing on 2006-09-15
I had a similar, very annoying problem. If I remember correctly, I eventually solved it by unintalling everything using aptitude, and manually deleting all traces of mysql, including the my.cnf and /var/run/mysql stuff.

---

### Post by locoHost on 2006-09-15
Is this it? Dump everything and restart? No other option?

How can I do this and not loose a large database?

---

### Post by ruedu on 2006-09-15
That is NOT a solution.  That's a typical windows solution.

MySQL is already running.  Try /etc/init.d/mysql stop   

When the script returns, do a killall -9 mysqld.  This will stop any remaining MySQL processes that might be around.  Double check with a ps aux | grep mysql.  You should get either no lines returned or just one (your ps aux).

Next, start the mysql daemon manualy with sudo mysqld.  You should get output similar to this.

```
 mysqld
060915 19:30:41  InnoDB: Started; log sequence number 0 43655
060915 19:30:41 [Note] mysqld: ready for connections.
Version: '5.0.22-Debian_0ubuntu6.06.2-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian Etch distribution

``` 
In another window, try connecting to mysql again, mysql -u root (if you haven't set any passwords in mysql) should connect you right up.  If all of this works, then you have some kind of startup script problem.

---

### Post by locoHost on 2006-09-16
Ok, I'm getting closer thanks to ruedu! ...

Here are my terminal windows...

mark@d6games:~$ sudo /etc/init.d/mysql stop
Password:
Stopping MySQL database server: mysqld.
mark@d6games:~$ ps aux|grep mysql
mark      8259  0.0  0.1   2876   800 pts/0    S+   11:07   0:00 grep mysql
mark@d6games:~$ sudo mysqld
060916 11:08:35  InnoDB: Started; log sequence number 0 43655
060916 11:08:35 [Note] mysqld: ready for connections.
Version: '5.0.22-Debian_0ubuntu6.06.2-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian Etch distribution

In another window...

mark@d6games:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
mark@d6games:~$

I tried mysql -u root -p and entered every variation of my password I can think of but everytime I get...

mark@d6games:~$ mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
mark@d6games:~$ mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
mark@d6games:~$ mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
mark@d6games:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
mark@d6games:~$ mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
mark@d6games:~$ mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
mark@d6games:~$

Does this mean I have a password set that I just can't remember? If yes, how do I clear it? I tried to clear it before based on a post at mysql.com and this is what eventually started the "mysqld.sock file missing error" I was just fighting through. What should I do next?

Thanks a ton for the replies guys :-)

---

### Post by locoHost on 2006-09-16
I'm in!!!!

ruedu's post got me started then I remembered my root password ;-)

Thank you, thank you, thank you, thank you, thank you for the replies!

:-)

---

### Post by sultanoswing on 2006-09-18
Good one!

My way would have worked too, ruedu ;)

(at least it did for me, although I only had a single, small database - my amarok one - to rebuild)

---

### Post by ruedu on 2006-09-18
> **sultanoswing said:**
> Good one!

My way would have worked too, ruedu ;)

(at least it did for me, although I only had a single, small database - my amarok one - to rebuild)

I'm not sure it would have because the password for root is stored in the mysql database which is stored in /var/lib/mysql (on Red Hat based systems anyway)  Blowing away the /var/lib/mysql directory would have killed all other databases.

---

### Post by topquarck on 2006-09-29
I tried this solution but I found the following problem:

060929 12:27:09  InnoDB: Started; log sequence number 0 43655
060929 12:27:09 [Note] Recovering after a crash using /var/log/mysql/mysql-bin
060929 12:27:09 [Note] Starting crash recovery...
060929 12:27:09 [Note] Crash recovery finished.
060929 12:27:09 [ERROR] Fatal error: mysql.user table is damaged or in unsupported 3.20 format.

and when I connect from another window I get the same old message of mysqld.sock

---

### Post by johnusa on 2006-10-13
I had the same problem and tried the suggestion from **ruedu**.  I was able to connect to mysql from another terminal window.  The implication now is that I have a problem with the startup script.
1. What startup script is ruedu referring to (name & location of script)?
2. What may be the problem with the script?
3. In the first terminal window in which I issued the **mysqld** command, the cursor goes to the next line every time I press the Enter key.  The only thing I seem to be able to do in this window is to close it.  I cannot get back to the shell prompt after issuing the **mysqld** command.

Thanks in advance for any help.

---

### Post by Pedro Miguel Rendeiro de on 2006-10-20
I have the same problem but i didn't set any root password and it gives alwais access denied.](*,) Can anybody help me?!?!?



> **locoHost said:**
> Ok, I'm getting closer thanks to ruedu! ...

Here are my terminal windows...

mark@d6games:~$ sudo /etc/init.d/mysql stop
Password:
Stopping MySQL database server: mysqld.
mark@d6games:~$ ps aux|grep mysql
mark      8259  0.0  0.1   2876   800 pts/0    S+   11:07   0:00 grep mysql
mark@d6games:~$ sudo mysqld
060916 11:08:35  InnoDB: Started; log sequence number 0 43655
060916 11:08:35 [Note] mysqld: ready for connections.
Version: '5.0.22-Debian_0ubuntu6.06.2-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian Etch distribution

In another window...

mark@d6games:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
mark@d6games:~$

I tried mysql -u root -p and entered every variation of my password I can think of but everytime I get...

mark@d6games:~$ mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
mark@d6games:~$ mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
mark@d6games:~$ mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
mark@d6games:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
mark@d6games:~$ mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
mark@d6games:~$ mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
mark@d6games:~$

Does this mean I have a password set that I just can't remember? If yes, how do I clear it? I tried to clear it before based on a post at mysql.com and this is what eventually started the "mysqld.sock file missing error" I was just fighting through. What should I do next?

Thanks a ton for the replies guys :-)

---

### Post by wirelessmonkey on 2006-10-21
Easy enough... It appears as though your mysql root password has been set somehow.  

From [http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html)

This is the dirty way to reset it

   1.

      Stop mysqld and restart it with the --skip-grant-tables --user=root options (Windows users omit the --user=root portion).
   2.

      Connect to the mysqld server with this command:

      shell> mysql -u root

   3.

      Issue the following statements in the mysql client:

      mysql> UPDATE mysql.user SET Password=PASSWORD('newpwd')
          ->                   WHERE User='root';
      mysql> FLUSH PRIVILEGES;

      Replace “newpwd” with the actual root password that you want to use.
   4.

      You should be able to connect using the new password.

---

