---
title: "changeing permissions"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-07-17
here are a set of permissions in etc/news

how to change all of them from root  root
to news  news

and etc/news has all root permissions
total 296
drwxr-xr-x 3 root root 4096 2006-07-11 12:23 .
drwxr-xr-x 90 root root 4096 2006-07-17 06:02 ..
-rw-r--r-- 1 root root 155 2006-03-15 10:39 actsync.cfg
-rw-r--r-- 1 root root 382 2006-03-15 10:39 actsync.ign
-rw-r--r-- 1 root root 304 2006-03-15 10:39 buffindexed.conf
-rw-r--r-- 1 root root 87179 2006-07-11 14:20 control.ctl
-rw-r--r-- 1 root root 859 2006-03-15 10:39 cycbuff.conf
-rw-r--r-- 1 root root 495 2006-03-15 10:39 distrib.pats
-rw-r--r-- 1 root root 1424 2006-03-15 10:39 expire.ctl
drwxr-xr-x 2 root root 4096 2006-06-29 11:37 filter
-rw-r--r-- 1 root root 5353 2006-03-15 10:39 incoming.conf
-rw-r--r-- 1 root root 4831 2006-07-10 18:42 inn.conf
-rw-r--r-- 1 root root 3179 2006-03-15 10:39 innfeed.conf
-rw-r--r-- 1 root root 72395 2006-03-15 10:39 innreport.conf
-rw-r--r-- 1 root root 2120 2006-03-15 10:39 innwatch.ctl
-rw-r--r-- 1 root root 1158 2006-03-15 10:39 moderators
-rw-r--r-- 1 root root 185 2006-03-15 10:39 motd.news
-rw-r--r-- 1 root root 609 2006-03-15 10:39 news2mail.cf
-rw-r--r-- 1 root root 5007 2006-07-05 14:26 newsfeeds
-rw-r--r-- 1 root root 516 2006-03-15 10:39 nnrpd.track
-rw-r--r-- 1 root root 583 2006-03-15 10:39 nntpsend.ctl
-rw-r--r-- 1 root root 4939 2006-03-15 10:39 ovdb.conf
-rw-r--r-- 1 root root 340 2006-03-15 10:39 overview.fmt
-rw-r----- 1 root news 597 2006-03-15 10:39 passwd.nntp
-rw-r--r-- 1 root root 1784 2006-03-15 10:39 radius.conf
-rw-r--r-- 1 root root 4898 2006-07-11 09:20 readers.conf
-rw-r--r-- 1 root root 911 2006-03-15 10:39 send-uucp.cf
-rw-r--r-- 1 root root 1430 2006-03-15 10:39 storage.conf
-rw-r--r-- 1 root root 114 2006-03-15 10:39 subscriptions


lex1

---

### Post by kabus on 2006-07-17
```
chown news:news /etc/news/*
```

Better be sure that you really need to do that, though.

---

### Post by lex1 on 2006-07-17
what reasons come to mind why I sholud not change the permissions?

what i am trying to do is that there is a user news and i am log in as lex1
but i want news to be the user not lex1.

everytime i get mail from news server (i am running a news server or trying to) it comes to lexi i want it to come to news.


lex1

---

### Post by kabus on 2006-07-17
> **lex1 said:**
> what reasons come to mind why I sholud not change the permissions?


Did you install the news server from the Ubuntu repositories and was /etc/news created automatically with those permissions? If so, you probably should leave it alone.

> **lex1 said:**
> 
everytime i get mail from news server (i am running a news server or trying to) it comes to lexi i want it to come to news.


That sounds like an issue that could be solved through some configuration setting. You'll probably get a better answer if you ask in the  [server forum]("http://ubuntuforums.org/forumdisplay.php?f=45").

---

### Post by lex1 on 2006-07-17
ok this maybe a sort of solution but I think I made a mistake a while back as i installed apt-get as root so perhaps news is the correct way to go ie changing permissions to from root to news.

lex1

---

