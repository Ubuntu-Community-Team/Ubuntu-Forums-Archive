---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Ubukanuba on 2007-03-17
help please I am trying to get my satelite card back up and I cant download or install the proper software.  In fact I cant install anything because I keep getting this error when I try!  what do I need to do? Sorry I am a complete nOoB and need real help, possibly mental help after the last 24 hours straight of trying to get this fixed with searches not helping at all.........SOS save our system!!  gracias

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


---

### Post by oilchangeguy on 2007-03-17
open a terminal and type what the message says to type.

---

### Post by Sef on 2007-03-17
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Open your terminal (Applications > Assessories > Terminal.)  Then type in this

```
sudo dpkg --configure -a
```

That should take care of your problems.

> Sorry I am a complete nOoB and need real help

No worries, we were all noobs at one time.

---

### Post by Ubukanuba on 2007-03-17
> Setting up mythtv-database (0.20-0.2ubuntu2) ...
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
Setting up kopete (3.5.5+kopete0.12.3-0ubuntu2.2) ...

dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.20-0.2ubuntu2); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-database
 mythtv



no idea?  How do i configure mythtv-database??

---

