---
title: "MySQL Scheduled Backups not Working?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by jjsonp on 2008-01-13
I have installed MySQL Server 5.0 on Ubuntu 7.10; it works fine.

However, when I create a new backup job and schedule it, it never works. If I click 'backup now' it works, but setting the schedule *seems* to work yet the backup doesn't run.

I've tried running mysql-admin as root and scheduling but it still won't run. Any help appreciated!

---

### Post by vikram on 2008-01-14
not used MySQL but can you put the commands to create backup in a script ?

If yes you can use cron to run the scripts or put a link to the script in 

/etc/cron.hourly
/etc/cron.daily
/etc/cron.weekly
/etc/cron.monthly
hope this helps

---

### Post by amorangi on 2008-05-08
Anyone? I'm getting the same problem - the scheduled backup appears to work, but the resultant file just contains
```
-- MySQL Administrator dump 1.4
--
-- ------------------------------------------------------
-- Server version	5.0.51a-3ubuntu5


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;

/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
```

But if I click the backup button everything works fine.

---

