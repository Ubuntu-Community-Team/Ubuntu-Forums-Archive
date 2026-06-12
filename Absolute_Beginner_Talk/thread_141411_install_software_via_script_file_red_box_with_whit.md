---
title: "install software via script file/ red box with white cross plus lock smybol"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-08
I have just installed a programme by running 
root@lex1# sh ./Install


I notice that where in the directory where the files are for this programme
each file has a red box with a white cross in it and a lock symbol at the foot
of each file. why is this?



lex1;) ;)

---

### Post by LordBug on 2006-03-08
Means the files are read-only.  For program files, this is generally a good thing.  Means you can't overwrite them on accident :)

---

### Post by Moebius on 2006-03-08
It seems that you have installed it as root, but you were viewing your files through Nautilus as "standard" user.

That red box and white cross is a quick way of Nautilus showing you what are those file permissions.

File permissions in UNIX environments are a very powerfull feature to grant of prohibit access in READ, WRITE and EXECUTE modes to those files.

---

