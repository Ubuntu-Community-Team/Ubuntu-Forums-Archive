---
title: "Enemy Territory 2.55 ?"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by trill on 2007-01-14
Hallo! I'm new to linux/ubuntu. So far I really like it but I cant't get ET 2.55 to install. I got 2.60b to to install and got the sound working,but I need to be on 2.55 where my clan is.This is what i get when I try to install....

Verifying archive integrity... all good
uncompressing enemy territory 2.55...........................................
......................
it is recommended to install as superuser
password:
su: authentication failure
sorry.
home/br/.setup10266: error while loading shared libraries: libgtk-1.2.so.0:can
not open shared object file: no such file or directory
./setup.sh: line 143: 10298 segmentation fault      "$setup" $@" 2>>$NULL
the setup program seems to have failed on x86/glibc-2.1
see [http://zerowing.idsoftware.com/linux](http://zerowing.idsoftware.com/linux)   for troubleshooting


well i went to that site and they pretty much just tell me to update. anyone herer running 2.55? or maybe a patch selector? I'd hate to buy windows just to play ET 2.55 being its really the only game i play.

---

### Post by rabid9797 on 2007-01-14
you need to install libgtk

```

sudo apt-get install libgtk1.2

```

also, make sure you are in superuser, i see that you didn't get into it, and that can cause problems.

---

### Post by trill on 2007-01-14
DANKE! :mrgreen: :mrgreen: :mrgreen:

---

### Post by rabid9797 on 2007-01-14
glad i could help

---

