---
title: "Gutsy?Dapper?Feisty? Which do I have?"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by ekimnarfnas on 2007-12-03
My first post is an elementary question...

I've been a Linux user for some time, but I'm new to 64bit Ubuntu.

This is my uname -a:
Linux michael-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

I'm trying to get flashplayer working on my AMD-64 box. I'm aware that my version of Ubuntu isn't the most recent one. I'm also aware that there are some configuration issues involved in getting flash working on 64bit CPUs. 

I've googled around and found this thread:

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

I've now got the file to set flash up but when I start the installation script I am asked what version of Ubuntu I have. I can't tell from uname -a whether I'm Gutsy, Dapper or Feisty. 

Can anyone help?

Thanks,

---

### Post by DirtDawg on 2007-12-03
Unless you are using the server version (no GUI), you can use 'System>About Ubuntu.' There should be version information on the first page.

---

### Post by philinux on 2007-12-03
System>admin>system monitor

Then click the system tab

---

### Post by caffienefree on 2007-12-03
One trick to keep in mind (the others work as well) is to open up a terminal and type "cat /etc/issue" (without the quotes).

8.04=hardy
7.10=gutsy
7.04=feisty
6.10=edgy
6.04=dapper

---

### Post by ekimnarfnas on 2007-12-04
Thanks all!!

michael@michael-desktop:~$ cat /etc/issue
Ubuntu 7.10 \n \l

michael@michael-desktop:~$ 

I'm gutsy.

---

### Post by coolbrook on 2007-12-04
2.6.22-14 = Gutsy

---

### Post by LowSky on 2007-12-04
> **ekimnarfnas said:**
> 
This is my uname -a:
Linux michael-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
  

2.6.22-14 is gutsy aka 7.10

---

### Post by silverhair on 2008-03-01
> **caffienefree said:**
> One trick to keep in mind (the others work as well) is to open up a terminal and type "cat /etc/issue" (without the quotes).

8.04=hardy
7.10=gutsy
7.04=feisty
6.10=edgy
6.04=dapper

I hope this is the right way to do this post thing?

I see the names dapper thru hardy and the numbers with them.  but what do they mean to a new user like me

---

### Post by zvacet on 2008-03-01
```
lsb_release -a
```

---

