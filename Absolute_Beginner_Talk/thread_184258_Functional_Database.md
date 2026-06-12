---
title: "Functional Database"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by camRW on 2006-05-29
Hello, I am extremely new to Linux/Ubuntu and I need to create a database that someone can access through the internet.  So far I've installed apache (it works), but I haven't the slightest clue what to do next.  I've searched for quite awhile, and the best answers I can find are installing PHP and MySQL on my apache server.  I don't know how to do this yet, so could someone point me in the right direction?  And if it means anything I've already created the database in OpenOffice's Base application.  Any help will be much appreciated.

Cheers,
Cameron

---

### Post by nemin on 2006-05-29
Database-systems like (I think) you mean, are usually built of two pieces: a backend and a frondend. 
The backend is the actual database, the data source. You can use MySQL for that.
Then, you need a frondend to access the database. That could be a webpage, build with PHP and running on Apache. For installation help, please see [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP).

I hope this clears things up for you.

---

### Post by camRW on 2006-05-29
Ah, thank you.  But now is there anyway I can use the database I have already created in OpenOffice's program or will I have to learn MySQL and create it from scratch?

---

