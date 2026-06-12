---
title: "mySQL won't start"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by visionviper on 2007-03-30
I have been looking for several days now on a way to fix my problem, but I am yet to find something that works.

```

 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have tried commenting out "skip innodb", I have tried changing the bind address to localhost (it apparently worked for someone), and I have tried going into synaptic, selecting mysql-server-5.0 and selecting configure, but I never get to any sort of config screen. I am running on a wireless internet connection, which from what I understand, for some reason may cause problems with mySQL.

---

### Post by HellSpawn on 2007-03-31
Have you tried uninstalling MySQL from Synaptics and re-installing?? It seems that you missed a dependency somewhere. 

Try installing from apt-get or aptitude instead.

I have used MySQL in wireless, wired and with no network without problems.

---

### Post by Mateo on 2007-04-07
mine won't work either.  ithink because I don't have a mysqld.sock file.  why don't I have this file and where can I get it?

```
Apr  7 18:51:32 matthew-desktop /etc/init.d/mysql[9790]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Apr  7 18:51:32 matthew-desktop /etc/init.d/mysql[9790]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Apr  7 18:51:32 matthew-desktop /etc/init.d/mysql[9790]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Apr  7 18:51:32 matthew-desktop /etc/init.d/mysql[9790]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Apr  7 18:51:32 matthew-desktop /etc/init.d/mysql[9790]: 
Apr  7 18:55:11 matthew-desktop mysqld_safe[10157]: started
Apr  7 18:55:11 matthew-desktop mysqld[10161]: 070407 18:55:11  InnoDB: Started; log sequence number 0 43655
Apr  7 18:55:11 matthew-desktop mysqld[10161]: 070407 18:55:11 [Note] Recovering after a crash using /var/log/mysql/mysql-bin
Apr  7 18:55:11 matthew-desktop mysqld[10161]: 070407 18:55:11 [Note] Starting crash recovery...
Apr  7 18:55:11 matthew-desktop mysqld[10161]: 070407 18:55:11 [Note] Crash recovery finished.
Apr  7 18:55:11 matthew-desktop mysqld[10161]: 070407 18:55:11 [ERROR] Fatal error: Can't open and lock privilege tables: Can't find file: 'host' (errno: 2)
Apr  7 18:55:11 matthew-desktop mysqld_safe[10172]: ended
Apr  7 18:55:25 matthew-desktop /etc/init.d/mysql[10337]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Apr  7 18:55:25 matthew-desktop /etc/init.d/mysql[10337]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Apr  7 18:55:25 matthew-desktop /etc/init.d/mysql[10337]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Apr  7 18:55:25 matthew-desktop /etc/init.d/mysql[10337]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Apr  7 18:55:25 matthew-desktop /etc/init.d/mysql[10337]: 
```

---

### Post by Gina on 2007-04-07
I had the same problem trying to get MythTV working (it uses the MySQL database).  I know nothing about MySQL and gave up.  I'd like to sort it out sometime though.

---

### Post by az on 2007-04-07
> **visionviper said:**
> I have been looking for several days now on a way to fix my problem, but I am yet to find something that works.

```

 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have tried commenting out "skip innodb", I have tried changing the bind address to localhost (it apparently worked for someone), and I have tried going into synaptic, selecting mysql-server-5.0 and selecting configure, but I never get to any sort of config screen. I am running on a wireless internet connection, which from what I understand, for some reason may cause problems with mySQL.

You have a package manager problem.  Did you mix repositories?

Try fixing the problem with

sudo apt-get -f install

Also, keep only one distro/release in your sources.list.  Do not mix.

---

### Post by Mateo on 2007-04-07
bump, how do you get mysqld.sock?

---

### Post by superm1 on 2007-04-08
> **az said:**
> You have a package manager problem.  Did you mix repositories?

Try fixing the problem with

sudo apt-get -f install

Also, keep only one distro/release in your sources.list.  Do not mix.
Completely seconded.  Clean up your sources.list.  Go into synaptic, reload the packages list and then find the "local" section in synaptic.  If you have anything listed there - you might want to try to roll back to the version in Ubuntu repository.  Pick that package and hit ctrl-e.  It will give you a list of available options.  Choose the one in ubuntu repositories.

---

### Post by visionviper on 2007-04-08
I have tried installing/uninstalling from synaptic and I have even followed two or three guides on how to install and set it up. I am yet to get anywhere. :(

---

### Post by superm1 on 2007-04-08
> **Gina said:**
> I had the same problem trying to get MythTV working (it uses the MySQL database).  I know nothing about MySQL and gave up.  I'd like to sort it out sometime though.
Gina, things should be much better for feisty in terms of mysql usernames and password issues people are running into.  After release in two weeks, definitely download a feisty disk and give things a shot.

---

### Post by visionviper on 2007-04-09
Well, I decided to try uninstalling mysql and reinstalling it one last time, and magically, it worked! What was different? I have no clue.

---

### Post by superm1 on 2007-04-09
> **visionviper said:**
> Well, I decided to try uninstalling mysql and reinstalling it one last time, and magically, it worked! What was different? I have no clue.
Hey as long as it works - I say great!

---

### Post by potterzot on 2007-04-13
same problem.  The lack of /var/run/mysqld/blah.sock I think is because mysqld doesn't start.  If I do sudo /etc/init.d/mysql start it fails.  Haven't figured out why yet except that it can't seem to connect to port 3306.

Any thoughts?

---

### Post by superm1 on 2007-04-14
> **potterzot said:**
> same problem.  The lack of /var/run/mysqld/blah.sock I think is because mysqld doesn't start.  If I do sudo /etc/init.d/mysql start it fails.  Haven't figured out why yet except that it can't seem to connect to port 3306.

Any thoughts?
Well the best place to *start* is /var/log/mysql/*.  See any logs there related to why its not starting. 

Also - check netstat -antp for anything else listening on 3306.

---

### Post by jonhowe on 2007-04-22
I was having this exact problem, and upon a restart of my computer mysql started successfully.

---

### Post by henriquemaia on 2007-05-04
> **jonhowe said:**
> I was having this exact problem, and upon a restart of my computer mysql started successfully.

I had the same issue and the reboot thing solved it. I wish I could understand what was going on to solve it more elegantly in the future.

---

### Post by henriquemaia on 2007-05-04
> **henriquemaia said:**
> I had the same issue and the reboot thing solved it. I wish I could understand what was going on to solve it more elegantly in the future.

Found it. I have a separate /var partition and it ran out of space (due to excessive mysql logs). Freeing the space solved this.

---

