---
title: "Sleuth kit on 7.10"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by knowlesy on 2008-03-11
hi, I need help generally installing it as i have no idea on the way to go around this since all install revolve around drapper drake any ideas please ??

---

### Post by zvacet on 2008-03-11
Before you do anything be sure that you have build-essential installed

```
sudo apt-get install build-essential
```

In case that you downloaded package on Desktop run** cd Desktop**

```
tar zxvf sleuthkit-2.51.tar.gz

```

That will unpack file and create folder.You have to be in that folder and you will do that by runing 

```
cd sleuthkit-2.51

```

Now you can start compile runing this commands

1. ./configure

2. make

3. sudo make install

---

### Post by knowlesy on 2008-03-25
its asking for several different packages i went and got these....
afflib-3.1.3
libewf-20070512
and then tried to install it then asked for another package.....
zlib-1.2.3
it was the libssl-dev package in which was missing however once i do a make install has it been installed on my system ?? ive tried to install sleuthkit with all of this and ill copy and paste the error 

```
In file included from img_open.c:26:
aff.h:19:20: error: afflib.h: No such file or directory
In file included from img_open.c:26:
aff.h:28: error: expected specifier-qualifier-list before 'AFFILE'
make[3]: *** [img_open.lo] Error 1
make[3]: Leaving directory `/home/vaux/Desktop/sleuthkit-2.51/tsk/img'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/vaux/Desktop/sleuthkit-2.51/tsk'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/vaux/Desktop/sleuthkit-2.51/tsk'
make: *** [all-recursive] Error 1

``` there seems to be a few errors previous but it would be a long post !

---

### Post by hankfong on 2008-06-26
knowlesy,

Have you had any luck with your install yet? I received your same error message but I was successful with my install tonight. Make sure you are logged in as _root_ user....hope this helps.

---

