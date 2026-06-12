---
title: "Mercury messenger"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by SMS on 2007-03-16
hey i recently installed java and mercury hoping it would all good like it was on gentoo linux, but i have been experiencing the same problems as loads of other people when you try to run mercury from the command line. then i was randomly throwing command and did this
> sms@sms-laptop:~$ sudo apt-get install mercury-messenger
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mercury-messenger is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mercury-messenger has no installation candidate
 
any ideas thanks in advance

---

### Post by v8YKxgHe on 2007-03-16
You may need to add more [Software Repositories]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html")

---

### Post by SMS on 2007-03-16
thanks for the responce but i dont know what respositories to add, any ideas

---

### Post by v8YKxgHe on 2007-03-16
> **SMS said:**
> thanks for the responce but i dont know what respositories to add, any ideas

Add both Universe and Multiverse.

---

### Post by SMS on 2007-03-16
they are both ticked 
that is what is confusing me
should i manually add some the /etc/.../sources.list

---

