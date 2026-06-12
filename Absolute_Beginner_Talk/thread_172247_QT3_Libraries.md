---
title: "QT3 Libraries?"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by Nice2Mitiu on 2006-05-08
ok, my problem is:
i'm trying to install a tarball, but in ./configure, i get the error of missing qt 3 libraries, or wrong path. I KNOW i have them. i tried ./configure --with-qt-libraries=/usr/lib/qt3/plugins/styles and some other dirs, but i continue getting similar errors. what can i do? i can't apt-get the program, but i need it, and i can't find a replasement.please help

---

### Post by louis_nichols on 2006-05-08
well, one of the first lessons one learns :)

when a configure script says it can't find library x, then you must have installed a package called either x-dev.deb or libx-dev.deb. Or in rpm-based distros, they will sometimes use x-devel.rpm or smth like that. 

In your case, it'll be libqt3-dev, if I remember well.

---

