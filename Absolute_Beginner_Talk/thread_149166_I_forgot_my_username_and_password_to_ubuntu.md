---
title: "I forgot my username and password to ubuntu"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by roadrunners on 2006-03-23
I forgot my username and password. Is there a way I find find it or atleast find the user name some how and I find find the password later.

---

### Post by Iowan on 2006-03-23
[http://ubuntuforums.org/showthread.php?t=142110&highlight=forgot+password]("http://ubuntuforums.org/showthread.php?t=142110&highlight=forgot+password")
In brief, boot into recovery mode, view /etc/passwd.  More details if you need them... good luck :)

---

### Post by Zar on 2006-03-23
[QUOTE=Iowan][http://ubuntuforums.org/showthread.php?t=142110&highlight=forgot+password]("http://ubuntuforums.org/showthread.php?t=142110&highlight=forgot+password")
In brief, boot into recovery mode, view /etc/passwd.  More details if you need them... good luck :)[/QUOTE]

There is a much simpler way ... :) 
Boot from live CD, display this document: /var/log/installer/cdebconf/questions.dat
(You can even open this document from a non-admin account.  Means, if you still have access to a non-admin account in your system, simply log on to it and open this document, you will not need live CD.)

Somewhere at the end of the document look for these entries:
Name: passwd/user-fullname
Name: passwd/user-password

You will find your username and password in plain English :-k

---

