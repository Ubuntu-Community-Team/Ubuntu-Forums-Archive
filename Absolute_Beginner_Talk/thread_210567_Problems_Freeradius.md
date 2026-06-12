---
title: "Problems Freeradius"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by lolstar on 2006-07-07
i installed freeradius using apt-get install freeradius

i configured the radius server that it will contact a mysql database.
but when i run freeradius in debug mode
freeradius -x
it gives an error at the bottom

rlm_sql (sql): Could not link driver rlm_sql_mysql: rlm_sql_mysql.so: cannot open shared object file: No such file or directory
rlm_sql (sql): Make sure it (and all its dependent libraries!) are in the search path of your system's ld.
radiusd.conf[14]: sql: Module instantiation failed.
radiusd.conf[1798] Unknown module "sql".
radiusd.conf[1727] Failed to parse authorize section.


in radiusd.conf it says the lib directory is : /usr/lib/freeradius

when i look into the dir i find alot of files but the file rlm_sql_mysql is missing

Can someone send me this file or dous somebody know a solution.
I'm using the newest ubuntu server and mysql 5.0

Greetz

---

### Post by Sigur on 2006-07-11
I have exactly the same problem. Anyone with a possible solution?

Lolstar, you found it?
:confused: :confused:

---

### Post by lolstar on 2006-07-11
you can install the file using

apt-get install freeradius-mysql

but it still dousnt seem to work
you can try it

somebody told me to install mysql developement libraries


greetz

---

### Post by Sigur on 2006-07-17
I finally uninstalled FreeRadius using the directions from [http://englanders.cc/~jason/howtos.php?howto=freeradius](http://englanders.cc/~jason/howtos.php?howto=freeradius) at the bottom of the page, and installed it again.
I hope it will help future ubuntuforums-crawlers!
It works fine now :D

---

### Post by toughstrong on 2006-11-04
You need to make some modification

In the /etc/init.d/freeradius file, change the first line:
[FONT="Courier New"]#!/bin/sh[/FONT]
to:
[FONT="Courier New"]#!/bin/bash[/FONT]

Problem solved.

---

