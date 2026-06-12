---
title: "mysql-server installation problems"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by Jettt900 on 2005-09-27
I'm not really completely new to linux, but I'm far from experienced. So- I felt this issue best fit in the noob area. I recently changed distros, so the debian/ubuntu feel is a lil different from what I'm used to.

Anyways, I mucked up my initial mySQL install, I set permissions wrong, and passwords wrong and I dunno, basically I messed it up and wanted to just start fresh and proper. I did a apt-get remove mysql-server and then just tried to re-install it, but it seemed to just find the old settings and set it up like it was before... so for some reason I decided I would delete all mysql related files in the /bin/ area, and then I went to etc/mysql/my.conf and deleted that, thinking now that it wouldn't see the config file it would give me a fresh install. Well... this is what I get when I try to install now:

```
tom@jbox:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
 mysql-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3555kB of archives.
After unpacking 9007kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package mysql-server.
(Reading database ... 67917 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_4.0.24-10ubuntu2_i386.deb) ...
Setting up mysql-server (4.0.24-10ubuntu2) ...
Stopping MySQL database server: mysqld.

WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.
Starting MySQL database server: mysqld...failed.
       Please take a look at the syslog.
/etc/init.d/mysql: line 102: /usr/bin/mysqladmin: No such file or directory
```

Looks like a bunch of badness. And this is basically the reason I felt it should go in this forum, as I am betting it's a pretty stupid mistake that I've made. heh.

Thanks for any help.

EDIT: Sorry, I missed the "This particular forum is for people who are new to Linux or new to computers in general. If you have previous experience with Linux (even if it just a little bit) or you have ever used the command line in your life to do tasks, then please find the appropriate forum area for your question."

I suppose then that a mod should move this thread to the Ubuntu server forum. Sorry for the hassle.

---

### Post by DJ_Max on 2005-09-27
What are your permissions and owners for /etc, /etc/mysql & the file my.cnf?

---

### Post by Jettt900 on 2005-09-27
[QUOTE=DJ_Max]What are your permissions and owners for /etc, /etc/mysql & the file my.cnf?[/QUOTE]

I ended up just doing a fresh install and properly configuring everything from the start this time.

So I'm all setup now. But thanks for the help anyways.

---

