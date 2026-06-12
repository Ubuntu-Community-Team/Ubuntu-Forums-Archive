---
title: "Total Linux Newb - Want Linux SQL server"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by TerribleTom on 2007-09-12
I know that this might sound more than a little ambitious...

I want to develop an SQL database using 100% (or as close to it as possible) open source software.

Ubuntu is one distribution I am considering.  MySQL is probably the leading contender for the database engine, though I am open to suggestion on both.

Currently, I have five databases in four locations - one location-specific database per location plus one 'headquarters' database that draws from the other four.

This is a point-of-sale/inventory control environment.  Presently, customers, suppliers and items are all global; transaction and inventory data are local.  I am not convinced that the present arrangement is the best possible design.  Thin clients and a single database could be very appealing.

Is Ubuntu a good choice for a database server?
Is Ubuntu a good choice for a thin client environment?

If you have any Linux/SQL experience, any advice you can offer a Linux beginner would be appreciated - especially with regard to MySQL on Ubuntu.

---

### Post by indytim on 2007-09-12
My recommendation is to go ahead and install LAMP.  Can be installed via a server build or on top of either Ubuntu or Kubuntu (if you want to use a graphical interface).  I've got it running on 3 different installations of Kubuntu.

Here's a pretty good how-to on the LAMP install:

[https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP")

IndyTim

---

