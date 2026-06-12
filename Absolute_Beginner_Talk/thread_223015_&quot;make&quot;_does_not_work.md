---
title: "&quot;make&quot; does not work?"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by cyme on 2006-07-25
hi there i tryed to install cdemu to mount my bin files. im swedish so you will notice lack of skill in english :D.

okey i started whit this 

cyme@cyme-desktop:~$ wget "http://robert.private.outertech.com/virtualcd/cdemu-0.7.tar.bz2"
--01:58:00--  [http://robert.private.outertech.com/virtualcd/cdemu-0.7.tar.bz2](http://robert.private.outertech.com/virtualcd/cdemu-0.7.tar.bz2)
           => `cdemu-0.7.tar.bz2'
Slår upp robert.private.outertech.com... 212.112.235.6
Ansluter till robert.private.outertech.com|212.112.235.6|:80... ansluten.
HTTP-begäran skickad, väntar på svar... 200 OK
Längd: 23 038 (22K) [application/x-tar]

100%[====================================>] 23 038        --.--K/s

01:58:00 (161.34 KB/s) - "cdemu-0.7.tar.bz2" sparad [23038/23038]

okey so far so good den i did this.


cyme@cyme-desktop:~$ tar xvfj cdemu-0.7.tar.bz2
cdemu-0.7/
cdemu-0.7/ChangeLog
cdemu-0.7/AUTHORS
cdemu-0.7/COPYING
cdemu-0.7/Makefile
cdemu-0.7/INSTALL
cdemu-0.7/libcdemu.py
cdemu-0.7/README
cdemu-0.7/TODO
cdemu-0.7/cdemu
cdemu-0.7/cdemu.c
cdemu-0.7/cdemu.h
cdemu-0.7/tarball.sh
cdemu-0.7/cdemu_kernel.h
cdemu-0.7/create_cdemu_devs.sh
cdemu-0.7/rpm/
cdemu-0.7/rpm/cdemu.spec
cyme@cyme-desktop:~$

after that im confused????(notice this is in swedish)
cyme@cyme-desktop:~/cdemu-0.7$ make
make: *** Ingen regel för att skapa målet "cdemu.ko", som behövs till "modules".  Stannar.

how can i fix this??

---

### Post by ndyguy on 2006-07-25
It's hard to say what is wrong from what you posted since it is not in English, you might get more help on the Swedish forums.  [http://ubuntu-se.org/forum/]("http://ubuntu-se.org/forum/")

---

### Post by peteguhl on 2006-08-24
Sounds like the same thing that's happening here:
[http://www.ubuntuforums.org/showthread.php?t=189891&highlight=cdemu](http://www.ubuntuforums.org/showthread.php?t=189891&highlight=cdemu)

Make sure to install linux-headers for your kernel.

---

### Post by aysiu on 2006-08-24
Ubuntu doesn't come with *make*. You need to install it: ```
sudo aptitude update
sudo aptitude install build-essential
```

---

