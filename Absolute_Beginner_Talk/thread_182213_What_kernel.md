---
title: "What kernel?"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by johanhartman on 2006-05-25
What kernel does ubuntu 5.10 use?

---

### Post by bruce89 on 2006-05-25
2.6.12

---

### Post by 23meg on 2006-05-25
2.6.12-10 by default. You can find what kernel you're using at any time with the following command:```
uname -r
```

---

### Post by uzi09 on 2006-05-25
also try
```
 uname -a 
```
to see a lot more info about your Ubuntu :D

---

### Post by johanhartman on 2006-05-25
thx

---

### Post by Sef on 2006-05-25
> 
Code:

uname -a

to see a lot more info about your Ubuntu 

> 2.6.12-10 by default. You can find what kernel you're using at any time with the following command:
Code:

uname -r



The difference between them is that uname -r gives you only the kernel number and uname -a combines all the system information from other options.  (Linux in a Nutshell, 5th ed., p. 491.)

From my computer:

> sef@jokat1:~$ uname -r
2.6.15-23-386

sef@jokat1:~$ uname -a
Linux jokat1 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux


---

