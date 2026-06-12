---
title: "Almost installed ... still need a nudge"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Samurai Penguin on 2008-03-23
trying to install gPhoto2 so I can hopefully get my Vivitar Vivicam 3330 pictures
transfered to the hdd. Worked through some needs (installing files via synaptic)
but the following has me stumped

tomana@HAL:~/Desktop/gphoto2-2.4.0$ make install
Making install in m4m
make[1]: Entering directory `/home/tomana/Desktop/gphoto2-2.4.0/m4m'
make[2]: Entering directory `/home/tomana/Desktop/gphoto2-2.4.0/m4m'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/tomana/Desktop/gphoto2-2.4.0/m4m'
make[1]: Leaving directory `/home/tomana/Desktop/gphoto2-2.4.0/m4m'
Making install in contrib
make[1]: Entering directory `/home/tomana/Desktop/gphoto2-2.4.0/contrib'
make[2]: Entering directory `/home/tomana/Desktop/gphoto2-2.4.0/contrib'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/tomana/Desktop/gphoto2-2.4.0/contrib'
make[1]: Leaving directory `/home/tomana/Desktop/gphoto2-2.4.0/contrib'
Making install in doc
make[1]: Entering directory `/home/tomana/Desktop/gphoto2-2.4.0/doc'
make[2]: Entering directory `/home/tomana/Desktop/gphoto2-2.4.0/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1"
/bin/mkdir: cannot create directory `/usr/local/share/man/man1': Permission denied
make[2]: *** [install-man1] Error 1
make[2]: Leaving directory `/home/tomana/Desktop/gphoto2-2.4.0/doc'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/tomana/Desktop/gphoto2-2.4.0/doc'
make: *** [install-recursive] Error 1


why is permission denied at /bin/mkdir ? What's error 1 and error 2 ?

---

### Post by Darganot on 2008-03-23
you need root access to get into anything under /bin or /usr

> sudo make install

---

### Post by teaker1s on 2008-03-23
possibly because it needs  root privilages
code tag not working on forum today for me- but try code below

sudo make install

---

### Post by Samurai Penguin on 2008-03-23
Yes, of coarse! I got so used to using Root Terminal that when I switched
back I still thought I was in root. I gotts share this one ...

I was working for HP many years ago as a instrumentation repair Tech
and after what had to be a good hour of getting nowhere, regarding a fix,
a fellow tech came over, looked over my set-up. asked how I was doing and
smiled. I said I was struggling and couldn't figure why I wasn't getting any
stable voltages, Then he reached over and switched on the external PS I had 
earlier on connected to the main board. Come on now, I'll bet most all of you
reading this did the same or similar sometime during your career.

BTW, thanks

---

### Post by teaker1s on 2008-03-23
many times, :popcorn:

---

