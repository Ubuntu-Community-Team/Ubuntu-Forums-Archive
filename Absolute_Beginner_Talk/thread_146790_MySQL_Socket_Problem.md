---
title: "MySQL Socket Problem"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by bennybobw on 2006-03-19
I've been following [this guide]("https://wiki.ubuntu.com/MYSQL5FromSource") to install MySQL5 from source.  Everything seemed to be going okay, but now when I give the following command to start mysql, I'm getting this error:

```

/usr/local/mysql/bin/mysql -p
Enter password:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.socket' (2)
```

I only found [one post]("http://www.ubuntuforums.org/showthread.php?t=144318&highlight=mysql+socket") similar to this, but the problem there was a unix socket and I don't seem to have the same files that that person had.  Installing MySQL is proving to be a nightmare!  Any help would be appreciated.  Thanks in advance.

---

### Post by henriquemaia on 2006-03-19
Maybe you have tried everything, but everytime I install mysql on my computer, I have to remember myself to change the owner of the mysql data folder to

mysql:mysql 
(user:group)

Otherwise, I'll get the same error you have. Don't know if this helps, but hope so.

---

### Post by bennybobw on 2006-03-20
I think I changed the file permissions like I was supposed to, but I'm not sure.  I thought that the data directory was the one that I had to change, do I need to change all of them to my mysql?  The directions aren't very clear in the mysql documentation.  They assume you know what the file permissions should be.  Here's the output:
bennybobw@ubuntu:/usr/local/mysql$ ls -l
total 40
drwxr-xr-x  2 root  mysql 4096 2006-03-18 20:50 bin
**drwx------  4 mysql mysql 4096 2006-03-18 23:01 data**
drwxr-xr-x  3 root  mysql 4096 2006-03-18 20:50 include
drwxr-xr-x  2 root  mysql 4096 2006-03-18 20:50 info
drwxr-xr-x  3 root  mysql 4096 2006-03-18 20:50 lib
drwxr-xr-x  2 root  mysql 4096 2006-03-18 20:50 libexec
drwxr-xr-x  3 root  mysql 4096 2006-03-18 20:50 man
drwxr-xr-x  7 root  mysql 4096 2006-03-18 20:50 mysql-test
drwxr-xr-x  3 root  mysql 4096 2006-03-18 20:50 share
drwxr-xr-x  5 root  mysql 4096 2006-03-18 20:50 sql-bench

**And for the data directory:**
bennybobw@ubuntu:/usr/local/mysql$ sudo ls -l ./data
total 20572
-rw-rw----  1 mysql mysql 10485760 2006-03-18 23:01 ibdata1
-rw-rw----  1 mysql mysql  5242880 2006-03-18 23:01 ib_logfile0
-rw-rw----  1 mysql mysql  5242880 2006-03-18 21:26 ib_logfile1
drwx------  2 mysql mysql     4096 2006-03-18 20:51 mysql
-rw-rw----  1 mysql mysql    15119 2006-03-18 20:51 mysql-bin.000001
-rw-rw----  1 mysql mysql      117 2006-03-18 20:51 mysql-bin.000002
-rw-rw----  1 mysql mysql      117 2006-03-18 21:15 mysql-bin.000003
-rw-rw----  1 mysql mysql      117 2006-03-18 21:15 mysql-bin.000004
-rw-rw----  1 mysql mysql      117 2006-03-18 21:27 mysql-bin.000005
-rw-rw----  1 mysql mysql      255 2006-03-18 23:01 mysql-bin.000006
-rw-rw----  1 mysql mysql      114 2006-03-18 21:37 mysql-bin.index
drwx------  2 mysql mysql     4096 2006-03-18 20:51 test
-rw-rw----  1 mysql mysql     2029 2006-03-18 23:01 ubuntu.err


Thanks again for your help.

---

