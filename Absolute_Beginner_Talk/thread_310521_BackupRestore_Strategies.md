---
title: "Backup/Restore Strategies"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by the gnome on 2006-12-01
I have two boxes I need backed up.  One is my ubuntu dev box, and the other is a debian server that I administer remotely.  I'm trying to come up with the best way to handle backing these machines up.

Ideally, I'd like to plop a DVD/removable HDD into my machine before I go to bed at night and have it backup automagically. 

Should I just back up the entire system?  Just the data?

Right now the stuff I think I need backed up is:
Remote machine:
-/var/www/*  //all my supported web pages
-Subversion repositories
-mysql databases
-users


Dev Machine:
-email, mp3's, docs
-dev code
-dev DB


Maybe I'm just better off grabbing everything?  Also, what is the best way to restore everything should a disaster occur?

---

### Post by Amit Yaron on 2006-12-01
I suggest to only save what you cannot re-install.
If it might take too long to download from the web burn a CD or a DVD.
Otherwise you can back it up in some web sites, such as Yahoo! Briefcase.

---

### Post by newagelink on 2006-12-01
Yahoo Briefcase ... (googles it) 25 whole MB? No way ...

Why d'you recommend that? You could just use gmail and email yourself like 2 GB worth of files.

---

### Post by Boelcke on 2006-12-01
Without going into every detail of how I have my backups set, perhaps you should look into rsync.  I have an rscync script run as a daily cron job that backs up / (minus some stuff) to another hard drive.

---

