---
title: "ownership change"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-07-23
how to change ownerships of these so it changes
from admin admin  to news  news?


drwxrwxrwx 2 admin admin 4096 2006-07-23 09:59
-rw-rw-r-- 1 admin admin 1946 2004-10-27 13:37
-rw-rw-r-- 1 admin admin 56 2004-10-27 13:37 suckkillfile
-rwxrwxrwx 1 admin admin 122 2006-07-05 11:15 sucknewsrc.old


lex1

ps full printout:

total 24
drwxrwxrwx  2 admin admin 4096 2006-07-23 09:59 .
drwxr-xr-x 90 root  root  4096 2006-07-23 08:18 ..
-rw-rw-r--  1 admin admin 1946 2004-10-27 13:37 get-news.conf
-rw-rw-r--  1 admin admin   56 2004-10-27 13:37 suckkillfile
-rw-r--r--  1 admin admin  463 2006-07-22 08:55 sucknewsrc
-rwxrwxrwx  1 admin admin  122 2006-07-05 11:15 sucknewsrc.old

---

### Post by jjstwerff on 2006-07-23
normally in the command line:

chmod news:news <files>

sometimes with -R for recursive change of directory content.

Withing nautilus there seems to be a restriction that you cannot change a file owner away from the current user.

---

