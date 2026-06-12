---
title: "[SOLVED] how to find out what version of ubuntu i have[Solved]"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by nikef on 2007-10-19
sorry about the daft post,but i can not do a search,its playing up

how do i find out what version i am in ?

---

### Post by oilchangeguy on 2007-10-19
system, about ubuntu

---

### Post by Paul820 on 2007-10-19
System->Administration->System Monitor then click the system tab. Much more detailed.

---

### Post by Sef on 2007-10-19
> sorry about the daft post,but i can not do a search,its playing up

It is not a daft post.  You are asking which is better than not asking.   By asking you learn.

---

### Post by tcort on 2007-10-19
If you're a command line person try **lsb_release**...

```
$ lsb_release -i -d -r -c
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
```

---

### Post by oilchangeguy on 2007-10-19
> **Paul820 said:**
> System->Administration->System Monitor then click the system tab. Much more detailed.

if all that is needed is simply the version. more detail is not needed.

---

### Post by nikef on 2007-10-19
thank you both
i have tried that and it gives me an introduction to ubuntu,and says thank you for your interest in ubuntu 7.10 gutsy gibbon ,released 18th october 2007

---

### Post by nikef on 2007-10-19
> **tcort said:**
> If you're a command line person try **lsb_release**...

```
$ lsb_release -i -d -r -c
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
```

thank you ,i have found it now 

trish@trish-desktop:~$ lsb_release -i -d -r -c
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
trish@trish-desktop:~$

---

### Post by nikef on 2007-10-19
Thanks to all,will mark solved  :)

---

### Post by Paul820 on 2007-10-19
> **oilchangeguy said:**
> if all that is needed is simply the version. more detail is not needed.

Calm down, he might find some information in there that he might want to use again, like hard drive space and the kernel, which that does show so i thought it might be usefull.

---

### Post by anasaz on 2007-11-21
OR simply you can do

cat /etc/issue

---

