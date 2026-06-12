---
title: "Help please with sound driver"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-07-15
I have an Intergrated sound on my mobo but I don't have any sound....So I went and got the latest als driver from there site.

When compiling and typing "make" I get an error



****@ubuntu:~/alsa-driver-0.4.0$ make
make[1]: Entering directory `/home/harry/alsa-driver-0.4.0/support'

Support code were sucessfully compiled.

make[1]: Leaving directory `/home/harry/alsa-driver-0.4.0/support'
make[1]: Entering directory `/home/harry/alsa-driver-0.4.0/kernel'
gcc -DALSA_BUILD -I/usr/src/linux/include -I.. -E -D__GENKSYMS__ persist.c | /sbin/genksyms > ../include/modules/persist.ver
/bin/sh: /sbin/genksyms: No such file or directory
In file included from ../include/driver.h:50,
                 from persist.c:23:
/usr/include/linux/config.h:1:2: error: #error "Compilation aborted. Please read the FAQ for linux-libc-headers package."
/usr/include/linux/config.h:2:2: error: #error "(can be found at http://ep09.pld-linux.org/~mmazur/linux-libc-headers/doc/)"
make[1]: *** [../include/modules/persist.ver] Error 127
make[1]: Leaving directory `/home/harry/alsa-driver-0.4.0/kernel'
make: *** [compile] Error 1
harry@ubuntu:~/alsa-driver-0.4.0$


Help is greatly appreciated

---

### Post by crispy_420 on 2006-07-15
What motherboard do you have? Let's start there.

---

### Post by zxcvbnm on 2006-07-15
I have an Asus P5LD2 Deluxe and I have the right linux headers

---

