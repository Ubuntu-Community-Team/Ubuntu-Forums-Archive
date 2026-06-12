---
title: "source compiling problem"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by internetishere on 2008-02-23
Ok so im trying to compile this game called BloodFrontier from its source heres the steps i do
i dl the .zip extract it to my desktop in a folder called BloodFrontier
i go to terminal i type and here what i do in terminal

teko@teko-desktop:~$ cd Desktop
teko@teko-desktop:~/Desktop$ cd BloodFrontier
teko@teko-desktop:~/Desktop/BloodFrontier$ cd src
teko@teko-desktop:~/Desktop/BloodFrontier/src$ make
cd enet; ./configure
/bin/sh: ./configure: Permission denied
make: *** [enet/Makefile] Error 126
teko@teko-desktop:~/Desktop/BloodFrontier/src$ 

permission denied??? how do i fix that so i can compile this????

---

### Post by Joeb454 on 2008-02-23
Be careful when using this, but type ```
sudo ./configure
```

It will ask for your password. Although it will not show any input when you type it :)

Hope this helps.

---

### Post by internetishere on 2008-02-23
> **Joeb454 said:**
> Be careful when using this, but type ```
sudo ./configure
```

It will ask for your password. Although it will not show any input when you type it :)

Hope this helps.

ok so this is what a typed and it didnt work

teko@teko-desktop:~$ cd Desktop
teko@teko-desktop:~/Desktop$ cd BloodFrontier
teko@teko-desktop:~/Desktop/BloodFrontier$ cd src
teko@teko-desktop:~/Desktop/BloodFrontier/src$ sudo ./configure
sudo: ./configure: command not found
teko@teko-desktop:~/Desktop/BloodFrontier/src$ 
if its any relivance i have build-essential and the make file is in the src folder

---

### Post by Joeb454 on 2008-02-23
I believe the syntax is ```
./configure
make
sudo make install
```

I'm assuming you left a space between "sudo" and "./configure" :p

---

### Post by taurus on 2008-02-23
Configure is in enet directory so run these two commands and post the output of the last one.

```
cd enet
ls -la
```

---

### Post by glennric on 2008-02-23
Do not do the "sudo ./configure" thing.  The program should not need superuser access to compile.
Have you checked the permissions on the file?  Is it executable?  If not type
```
chmod +x configure
```

---

### Post by internetishere on 2008-02-23
teko@teko-desktop:~/Desktop/BloodFrontier/src/enet$ ls -la
total 588
drwxr-xr-x  5 teko teko   4096 2007-09-19 20:21 .
drwxr-xr-x 13 teko teko   4096 2007-09-19 20:21 ..
-rw-rw-rw-  1 teko teko  31970 2006-09-18 12:32 aclocal.m4
-rw-rw-rw-  1 teko teko    964 2007-05-31 01:07 callbacks.c
-rw-rw-rw-  1 teko teko  44648 2006-03-06 22:56 config.guess
-rw-rw-rw-  1 teko teko  32792 2006-03-06 22:56 config.sub
-rw-rw-rw-  1 teko teko 175284 2006-12-12 21:27 configure
-rw-rw-rw-  1 teko teko   1239 2006-12-12 21:27 configure.in
drwxr-xr-x  2 teko teko   4096 2007-09-19 20:21 CVS
-rw-rw-rw-  1 teko teko  15727 2006-03-06 22:56 depcomp
-rw-rw-rw-  1 teko teko   5938 2006-03-06 22:56 design.txt
drwxr-xr-x  3 teko teko   4096 2007-09-19 20:21 docs
-rw-rw-rw-  1 teko teko  40444 2006-03-06 22:56 Doxyfile
-rw-rw-rw-  1 teko teko   4008 2006-03-06 22:56 enet.dsp
-rw-rw-rw-  1 teko teko  14250 2006-07-06 12:51 host.c
drwxr-xr-x  4 teko teko   4096 2007-09-19 20:21 include
-rw-rw-rw-  1 teko teko   5849 2006-03-06 22:56 install-sh
-rw-rw-rw-  1 teko teko   1067 2007-05-31 02:11 LICENSE
-rw-rw-rw-  1 teko teko   1160 2006-03-06 22:56 list.c
-rw-rw-rw-  1 teko teko    160 2006-03-06 22:56 Makefile.am
-rw-rw-rw-  1 teko teko  22349 2006-09-18 12:32 Makefile.in
-rw-rw-rw-  1 teko teko  10940 2006-03-24 14:14 missing
-rw-rw-rw-  1 teko teko    764 2006-03-06 22:56 mkinstalldirs
-rw-rw-rw-  1 teko teko   3577 2007-03-26 23:31 packet.c
-rw-rw-rw-  1 teko teko  25960 2007-01-06 19:04 peer.c
-rw-rw-rw-  1 teko teko  53901 2007-07-12 20:22 protocol.c
-rw-rw-rw-  1 teko teko    347 2006-03-14 17:18 README
-rw-rw-rw-  1 teko teko  11854 2006-03-06 22:56 tutorial.txt
-rw-rw-rw-  1 teko teko   9594 2007-06-01 04:19 unix.c
-rw-rw-rw-  1 teko teko   7808 2007-04-14 16:15 win32.c

teko@teko-desktop:~/Desktop/BloodFrontier/src/enet$ 

theres the output you asked for

---

### Post by taurus on 2008-02-23
```
chmod 755 configure
./configure
```

---

### Post by internetishere on 2008-02-23
> **taurus said:**
> ```
chmod 755 configure
./configure
```

huh???

---

### Post by mc4man on 2008-02-23
This may get you a little further - I think you have to compile enet first - from enet prompt 
```
aclocal && automake -a -c --foreign && autoconf
```
then ./configure  - make. ect. 
I think this is just the start of your problems but maybe the upcoming errors will have solutions

automake 1.7 may be most suitable version

here are some relevant notes
[http://www.linuxgames.com/archives/9586#comments](http://www.linuxgames.com/archives/9586#comments)

---

