---
title: "How do I CLEAN out anything that's LAMP related?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-05-23
I'm having problems configuring Apache like I'm used to from Windows XP.  I think it's because I had XAMPP on earlier which I uninstalled but there seems to be a bunch of conflicts after I aptitude installed LAMP.

Now I want to CLEAN out everything that's Apache+PHP+MySQL related so I can start from a clean slate.  Can someone structure a plan for doing so properly that I can follow?

---

### Post by az on 2007-05-23
start with

sudo apt-get remove apache* libapache* php* mysql-common mysql-server

see here to install and configure LAMP:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by jingo811 on 2007-05-23
Tnx the exorcism worked like clockwork. :popcorn: however when I look in /etc I still see the 4 folders from the past what should I do with them?
* apache
* apache2
* php4
* php5


I've been following that guide for a while now trying to do the config stuff for XAMPP and my old malfunctioned LAMP install.  I didn't like it's lack of direct instructions on how to actually install.  It just mentions some CLI code and then says install with any method.  I don't know any method only Synaptic but that wouldn't be correct.

So will this do the trick for my Dapper 6.06 Desktop?
```
**sudo aptitude install **apache2 php5-mysql libapache2-mod-php5 mysql-server
```

---

### Post by jingo811 on 2007-05-25
What should I do with these 4 folders in /etc?  They all still contain a bunch of important files it seems.

* apache
* apache2
* php4
* php5

---

### Post by jingo811 on 2007-05-28
bump 1.  

What should I do with the 4 folders mentioned above?  I'm still stuck in the process of cleaning out old malfunctioning LAMP.

---

### Post by jingo811 on 2007-06-04
bump 2.  Same as above!
I'll check with you one last time before I install it for real.  So there won't be any trouble ahead......because of the many old folders and files laying around.

---

### Post by coxy on 2007-06-05
```

sudo apt-get --purge remove package names

```

That would remove the config files as well as the packages.

---

### Post by jingo811 on 2007-06-05
tnx for the tips!

---

### Post by jingo811 on 2007-06-06
I finally got time to use that command I'm not sure if I'm using it right?
But it seems nothing happens should I DELETE those 4 catalogs manually instead to get rid of all old traces?

```
mike@sanka:/etc$ **sudo apt-get --purge remove apache**
Reading package lists... Done
Building dependency tree... Done
Package apache is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mike@sanka:/etc$ **sudo apt-get --purge remove apache2**
Reading package lists... Done
Building dependency tree... Done
Package apache2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mike@sanka:/etc$ **sudo apt-get --purge remove php4**
Reading package lists... Done
Building dependency tree... Done
Package php4 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mike@sanka:/etc$ **sudo apt-get --purge remove php5**
Reading package lists... Done
Building dependency tree... Done
Package php5 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mike@sanka:/etc$
```

---

