---
title: "How to install stuff"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by EDS Sucks on 2007-06-03
Hi,

I just installed dapper dan on a sony vaio, but I'm having some trouble installing things that I need.   I've had experience in the past with solaris, sunos, Red Hat, and Mandrake, and I'm frustrated here because I don't even have gcc available.   I'm **TOLD** I have
it istalled, but when I've tried to compile a simple "hello world" program it seems that stdio.h isn't even available.

```

eds_sucks@vaio:~$ sudo apt-get install gcc-4.0
Reading package lists... Done
Building dependency tree... Done
gcc-4.0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
eds_sucks@vaio:~$ gcc foo.c
bash: gcc: command not found
eds_sucks@vaio:~$ gcc-4.0 foo.c
foo.c:1:19: error: stdio.h: No such file or directory
foo.c:2:20: error: stdlib.h: No such file or directory
foo.c: In function &#8216;main&#8217;:
foo.c:5: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
eds_sucks@vaio:~$            

```

Can someone please tell me what I'm doing wrong?

Thank you.

---

### Post by taurus on 2007-06-03
You just need to install build-essential and that would install gcc for you.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by mlentink on 2007-06-03
You may want to read [this]("http://monkeyblog.org/ubuntu/installing/"), which helped me

---

### Post by Chayak on 2007-06-03
Hopefully someone else will comment specifics but  I believe you also need to install the build-essential package

---

