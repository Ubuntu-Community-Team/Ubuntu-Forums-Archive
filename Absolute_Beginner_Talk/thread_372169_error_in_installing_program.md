---
title: "error in installing program"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by black_ice on 2007-02-27
hello all.., 
i download jackel which is an msn client and it was with .tar.bz2 and i extract files when i want to run ./configure script on the extracted dir i got this errors

root@adam-laptop:/home/adam/MyDownloads/jackle# ./configure 
QTDIR is not set. Exiting.


and here is the install instructions 



- Make sure QMAKESPEC and QTDIR is set. QMAKESPEC will be something like
  linux-g++ or linux-g++-64
- Run ./configure and make sure it is successful in creating a Makefile.
- Run make
- Run install/install.sh

---

### Post by rjfioravanti on 2007-02-27
[http://kflog.org/pipermail/kflog-user/2006-September/000090.html](http://kflog.org/pipermail/kflog-user/2006-September/000090.html)

---

### Post by black_ice on 2007-02-27
where to find configure file with 7140 line ? 

To build on Debian / Ubuntu:

In the configure file - line 7140 - add path to the QT directory /usr/share/qt3

if test $kde_qtver = 3; then
  kde_qt_dirs="$QTDIR /usr/lib/qt3 /usr/lib/qt /usr/share/qt3"

---

### Post by rjfioravanti on 2007-02-27
sorry I thought you would read the whole article

you need to set the QTDIR environment variable for whatever script you are running

export QTDIR=/usr/share/qt3

---

### Post by black_ice on 2007-02-27
thanx for you but please if you can explain me what i will do in steps

---

### Post by rjfioravanti on 2007-02-28
open a terminal

do that export command like i said above

type in echo $QTDIR 
to ensure that it has been set

and now it is set, you can run your configure like you wanted to

---

