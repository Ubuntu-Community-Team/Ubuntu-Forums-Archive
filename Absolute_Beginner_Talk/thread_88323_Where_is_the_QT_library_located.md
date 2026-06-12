---
title: "Where is the QT library located?"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by maskkkk on 2005-11-10
I'm trying to compile kdissert.
(on 5.10)

When I try to run make it complains that:


scons: Reading SConscript files ...
Checking for kde-config           :  kde-config was found as /usr/bin/kde-config
Checking for kde version          :  3.4.3
Checking for the qt library       :  qt was not found
Please set QTDIR first (/usr/lib/qt3?) or try scons -h for more options

Where is the QTDIR?

Thanks, 

maskkkk

---

### Post by Remmelas on 2005-11-10
make sure you have libqt3-mt-dev installed

---

### Post by Remmelas on 2005-11-10
or easier, rather than compiling, install it from the repositories
sudo apt-get install kdissert

---

### Post by maskkkk on 2005-11-14
Nope they don't have it in the repositories. (Unless I don't know which one).

---

