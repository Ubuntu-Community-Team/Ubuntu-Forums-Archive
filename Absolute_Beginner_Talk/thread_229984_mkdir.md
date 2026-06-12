---
title: "mkdir"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-08-05
in this like below if www/www.example.com/cgi.bin do not exist is it
a case of
cd /var
mkdir www, [www.example.com](www.example.com), cgi-bin?



cp -p /usr/lib/cgi-bin/mailgraph.cgi /var/www/www.example.com/cgi-bin

---

### Post by rapha on 2006-08-05
What is your problem, what are you trying to accomplish that doesn't work? I'm not quite sure I understand your post...

---

### Post by lex1 on 2006-08-05
the directories **www/www.example.com/cgi-bin** do not exist so must create them.

lex1

---

### Post by moma on 2006-08-05
-p option :
$ sudo mkdir -p /var/www/www.example.com/cgi.bin

btw: is it cgi.bin or cgi-bin ?

---

### Post by rapha on 2006-08-05
Yes, the -p option would be the one to recursively create a directory tree. It normally is cgi-bin, with a dash (-).

---

