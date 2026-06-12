---
title: "How to safely purge an MYSQL database?"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by whein on 2008-04-09
I've been running a Myth TV box for a while now and over the course of several upgrades and updates things seem to have gotten royally FUBARed with the mysql database for it.  Uninstalling and reinstalling Myth is easy enough, but it seems to recognize that a database already exists and tries to use it instead of creating a fresh one.  Can someone provide me the correct steps and syntax to SAFELY delete the old mucked up table and either create a new one that Myth can use or I guess I'll just reinstall Myth and get it to create it for itself.

Note, I have already tried to repair the database using the magic
```

sudo -i
cd /var/lib/mysql/mythconverg
myisamchk -e *.MYI
myisamchk -r foo1.MYI
myisamchk -r foo2.MYI
myisamchk -r foo3.MYI
.
.
.

```
and it always says that it is repaired, but then a day later it barfs again.  Even when it showed no errors the mysqldump command complained and would not create backups.  Things got even more funkified a few days back when I upgraded to the newer version of Myth (I'm running Gutsy).  It said something about changing from version 0 to version 1024 and would I like to upgrade my database.  Since the db wasn't working so hot anyway I said yes and now I can't even launch Myth frontend.  I'd really like to avoid wiping the entire drive and reinstalling Ubuntu from scratch, so...  How can I fix this?  I am perfectly willing to loose all the existing records on what's been recorded, etc.  I just want to be functional moving forward.  :)

-Will

---

### Post by indytim on 2008-04-09
One recommendation is to get a working phpMyAdmin.  This will give you a web front end to the MySQL server running on your box.  From there, you can drop the offending database and let it re-institute it on the next run of your app.

I believe phpMyAdmin is in the repostories.

Cautionary note: don't delete any other databases as they are required for the MySQL server to run properly.

IndyTim

---

### Post by Cypher on 2008-04-09
If you  have your MySQL credentials, then enter MYSQL with
```

mysql -u<username> -p

```
Substitude your username for <username> and enter your password when prompted. At the mysq> prompt do
```

show databases;

```
This will list all the databases, once you find the MythTV database, you can delete it with
```

drop database <dbname>;

```
Now re-create the database with
```

create database <dbname>;

```
Obviously, <dbname> is the same in both of 2 last commands. You now have a brand new database and hopefully MythTV will realize it's a fresh database and create it's tables/schema..

---

