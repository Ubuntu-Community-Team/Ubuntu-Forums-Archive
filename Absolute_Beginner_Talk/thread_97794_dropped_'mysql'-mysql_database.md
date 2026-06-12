---
title: "dropped 'mysql'-mysql database"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by bassMonkey on 2005-12-01
Hi, I accidentally dropped my mysql -database when fiddling with phpmyadmin. Now I can't login with mysqladmin. I've f***ed it up real bad now haven't I? :( 
I have no backup or anything. Any suggestions?

--Edit--
Ok, I was told to do a "mysql_install_db", so I did, and it probably worked. But I still can't login...

--Edit2--
hmm, now i ran the postinstall script, didn't seem to do what it was supposed to do and got some errors. Still won't work (It didn't do anything bad though right?:confused:)

---

### Post by Robgould on 2005-12-01
I just saved a bunch on my car insurance!

---

### Post by Robgould on 2005-12-01
A little joke there....I don't know for sure, but I believe you are screwed.  I am sorry.

---

### Post by bassMonkey on 2005-12-01
I think so too... :( 
Oh well -> beer

---

### Post by simgish on 2005-12-01
Try running this from the command line:

mysqladmin password *your-password*

---

### Post by bassMonkey on 2005-12-02
That won't work because mysqladmin can't connect to to mysql: "'Access denied for user: 'debian-sys-maint@localhost'"

---

