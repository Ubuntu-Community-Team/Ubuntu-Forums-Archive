---
title: "kxdocker-1-1-4a"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by bobbyshafter on 2007-04-01
I currently running kubuntu edgy.I tried to install kxdocker using adept .

Cannot get kxdocker to run.

I then dl kxdocker-1.1.4a and tried to install using the terminal.

When i did the 'make' command i get the followering erro
  
usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make[2]: *** [libKXMouse.la] Error 1
make[2]: Leaving directory `/home/bobby/kxdocker-1.1.4a/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bobby/kxdocker-1.1.4a'
make: *** [all] Error 2

the configure work fine

any help ?

---

### Post by Kobalt on 2007-04-03
Did you uninstall completely kxdocker with apdet before compiling ? 
You can also try to run this command after ./configure and before make 
```
make clean
```

---

### Post by bobbyshafter on 2007-04-05
Tried that ..did not work

---

### Post by ramjet_1953 on 2007-04-05
Try KoolDock, it's much less painful.
Works find under KDE and GNOME.

Regards,
Roger :cool:

---

### Post by rebegin on 2007-05-03
installing debian packages worked for me:
[http://packages.debian.org/testing/x11/kxdocker](http://packages.debian.org/testing/x11/kxdocker)
[http://packages.debian.org/testing/x11/kxdocker-data](http://packages.debian.org/testing/x11/kxdocker-data)

---

