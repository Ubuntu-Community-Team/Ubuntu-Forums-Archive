---
title: "problem with make"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Ic3y on 2007-01-21
Hi guys
I am having a problem with make

> ticker.c:28:25: error: mysql/mysql.h: No such file or directory

I have a makefile and there is the above missing file can someone please tell me what I can do to access this file or directory

Thanks in advance
Ic3y :biggrin:

---

### Post by po0f on 2007-01-21
Ic3y,

Install [libmysqlclient15-dev](http://packages.ubuntu.com/edgy/libdevel/libmysqlclient15-dev) to get that header file.

---

### Post by Ic3y on 2007-01-21
thanks for that po0f it worked a treat

regards
Ic3y :biggrin:

---

