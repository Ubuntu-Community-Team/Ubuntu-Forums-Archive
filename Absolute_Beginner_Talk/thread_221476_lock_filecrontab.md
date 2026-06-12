---
title: "lock file\crontab"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-07-23
output from admin on cron job

lex1@xstation:~$ cd /home/admin
lex1@xstation:/home/admin$ suck nntp.aioe.org -A -bp -hl localhost -c -i 20
0 -M -n -Q
Invalid default read for new active group, must be <= 0
Unable to create Lock File /home/admin/suck.lock

----------------------------------------------------


how to create lock file?
the cron job is running in admin which does not have root access. but
has been addes to cron.allow file.

if i loginto admin it runs ok.but not from lex1?

suck dir looks like this
total 24
drwxrwxrwx  2 news  news  4096 2006-07-23 09:59 .
drwxr-xr-x 90 root  root  4096 2006-07-23 08:18 ..
-rw-rw-r--  1 news  news  1946 2004-10-27 13:37 get-news.conf
-rw-rw-r--  1 news  news    56 2004-10-27 13:37 suckkillfile
-rw-r--r--  1 admin admin  463 2006-07-22 08:55 sucknewsrc
-rwxrwxrwx  1 news  news   122 2006-07-05 11:15 sucknewsrc.old


lex1

---

### Post by jjstwerff on 2006-07-23
What happened is that cron starts the task as the 'news' user. But other users may not write into your directory but suck wants to create a lock file in it's current working directory.

I think the best solution is to create a sub directory of /home/admin like /home/admin/suck and change the cron job to:

cd /home/admin/suck

and allow the news user to change that directory. Normally only changing the group (chgrp -R news suck) of that directory to news and allow the group to write and read. (chmod g+rw <files>)

---

