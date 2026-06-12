---
title: "make install - getting an error"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by morwyn on 2007-06-16
I'm trying to install Taskbar V2 into my Kubuntu install, but I am getting the following error on make install:

/usr/bin/install: cannot create regular file `/usr/lib/libmtaskbar.so': Permission denied
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/morwyn/Desktop/mtaskbar/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/morwyn/Desktop/mtaskbar/src'
make: *** [install-recursive] Error 1

Being new to Ubuntu and Kubuntu, I am not quite sure what to try... I tried installing liblt libraries but that didn't help...

Anyone have any ideas?

---

### Post by plcdfa on 2007-06-16
Do you run make install as root? (sudo make install)

---

### Post by morwyn on 2007-06-16
stupidly, no - ty :oops:

---

### Post by NeoGreen on 2007-06-17
Man, that is crazy, I always thought that make install was a unix commmand.  I use it in FreeBSD.  That's cool

---

### Post by plcdfa on 2007-06-18
Well GNU/Linux is **not** Unix, but resembles it quite a lot. ;)

---

