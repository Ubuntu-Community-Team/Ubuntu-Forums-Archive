---
title: "sudo vs root user"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by shoki on 2006-08-09
Hello All,

Just wanted to ask what is the difference between running as root and sudo? It seems like if you can do root level things as sudo why wouldn't it be just as powerful and or dangerous as running as root?

I guess the fact that you have to send a password as sudo is one level of protection but what other good and bad points are there for and against root-user and sodu?

Thank you for your time,
--Shoki

---

### Post by firehazard17 on 2006-08-09
not much but ubuntu doesnt let you run as root

---

### Post by mozkaynak on 2006-08-09
Hi,
I think there is a big difference between being root and using sudo.

In both conditions you will have access to critical parts of the system. The difference is when you login as root you have access all the time but when you login as normal user and use sudo you can access only with you command with that you use sudo.

I think this provides great security at least for the users who are novice like me.

I dont see any negative point of sudo mechanism but the positive part is extra safety.

---

### Post by aysiu on 2006-08-09
Read this. It talks about the pros and cons of each model:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by meney on 2006-08-09
sudo makes you think before you press the enter key... ;)

Of course you can simply type su and become root in your terminal. I think sudo is the linux version of the 'do you really wan't to delete this?' in windows.

---

### Post by MaximB on 2006-08-09
if you are a windows user then :
su - you logged in (the terminal) as administrator.
sudo - you "run as administrator"

---

