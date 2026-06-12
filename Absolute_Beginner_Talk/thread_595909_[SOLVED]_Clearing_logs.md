---
title: "[SOLVED] Clearing logs"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by joeycbulk on 2007-10-29
Is it safe to clear logs by just deleting the files?
I'm afraid that some apps(e.g. Apache,mysql) I installed or ubuntu itself might stop working if files were missing.

---

### Post by ronald.higgins on 2007-10-29
Not the Mysql Bin logs :P

But normal operation logs can been cleared, or just echo "" > somefilename , that'll empty out the contents and leave the file intact.

---

### Post by PointyWombat on 2007-10-29
Typically not becuase something may have the file open for writing, and deleting it may cause further headaches.  You can either shut down the logging facility then smoke the log, or simply zero out the log with the command:

>somelog.log

---

### Post by joeycbulk on 2007-10-29
OK. Thanks to all! Linux rules! :guitar:

---

### Post by l0co on 2008-02-10
Depending on the cause of clearing you have to do something else as well - if you want just to save space, just go to /var/log and run "rm -r *.gz" - all old gzipped logs will be deleted. These files are not open by any process and after some time can take about 80% of /var/log size.

---

