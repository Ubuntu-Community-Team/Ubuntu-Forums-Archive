---
title: "mythtv install problem"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by jimbo650 on 2007-12-14
I am a new user and want to use mythtv with unbuntu 7.10
I have a mysql problem

see message on install:
Setting up libdbd-mysql-perl (4.004-2) ...
Setting up mysql-client-5.0 (5.0.45-1ubuntu3) ...

Setting up mysql-server-5.0 (5.0.45-1ubuntu3) ...
 * Stopping MySQL database server mysqld                                 [ OK ]
 * Starting MySQL database server mysqld                                 [ OK ]
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

Setting up libqt3-mt-mysql (3:3.3.8really3.3.7-0ubuntu11.1) ...
Setting up libmyth-0.20 (0.20.2-0ubuntu10) ...

Setting up mysql-client (5.0.45-1ubuntu3) ...
Setting up mysql-server (5.0.45-1ubuntu3) ...
Setting up mythtv-common (0.20.2-0ubuntu10) ...
adduser: Warning: that home directory does not belong to the user you are curren                                                                                      tly creating.

Setting up mythtv-database (0.20.2-0ubuntu10) ...
Failed to connect to database: Access denied for user 'root'@'localhost' (using                                                                                       password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database

Setting up mythtv-frontend (0.20.2-0ubuntu10) ...

Setting up mythtv-transcode-utils (0.20.2-0ubuntu10) ...
Setting up mythtv-backend (0.20.2-0ubuntu10) ...
udev active, devices will be created in /dev/.static/dev/
Starting MythTV server: mythbackend .

Setting up mythtv (0.20.2-0ubuntu10) ...
Setting up mythtv-themes (0.20-0.1ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
jim@multimedia:~$                                         

what should i do to correct this problem?

---

### Post by bone2006 on 2007-12-24
Is the primary purpose of your system a PVR? If so you might want to try mythbuntu at [www.mythbuntu.org](www.mythbuntu.org)
It's ubuntu 7.10 with xfce desktop or maybe another desktop other than gnome and mythtv already integrated for you.  I've installed mythtv on ubuntu 7.10 and it was a pain and if anything happened to my system that I had to load it again, I'd probably just go with mythbuntu installed.  It's based off of ubuntu 7.10

---

