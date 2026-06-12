---
title: "Lucent 56 Winmodem"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-22
i am following linmodems
and here is the problem:

```

shoaibi@saber-rider:~$ wget http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-8.tar.bz2
--14:37:38--  http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-8.tar.bz2
           => `ltmodem-2.6-alk-8.tar.bz2'
Connecting to 172.30.10.11:3128... connected.
Proxy request sent, awaiting response... 200 OK
Length: 436,392 (426K) [application/x-bzip2]

100%[====================================>] 436,392        1.08M/s             

14:37:38 (1.07 MB/s) - `ltmodem-2.6-alk-8.tar.bz2' saved [436392/436392]

shoaibi@saber-rider:~$ mkdir lucent
shoaibi@saber-rider:~$ mv ltmodem*.tar.bz2 ~/lucent
shoaibi@saber-rider:~$ cd lucent/
shoaibi@saber-rider:~/lucent$ tar -xjvf ltmodem*.tar.bz2
ltmodem-2.6-alk-8/
ltmodem-2.6-alk-8/NEWS
ltmodem-2.6-alk-8/docs/
ltmodem-2.6-alk-8/docs/README_10MDK
ltmodem-2.6-alk-8/docs/ltmodem.rules
ltmodem-2.6-alk-8/docs/udev-setup
ltmodem-2.6-alk-8/docs/Example.txt
ltmodem-2.6-alk-8/Makefile
ltmodem-2.6-alk-8/README
ltmodem-2.6-alk-8/lt_modem.c
ltmodem-2.6-alk-8/ltmdmobj.o-pre-8.31
ltmodem-2.6-alk-8/serial.c
ltmodem-2.6-alk-8/ltmdmobj.o
ltmodem-2.6-alk-8/DEFINES
ltmodem-2.6-alk-8/linuxif.h
ltmodem-2.6-alk-8/ltmdmobj.o-8.31
shoaibi@saber-rider:~/lucent$ sudo apt-get install wvdial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wvdial is already the newest version.
The following packages were automatically installed and are no longer required:
  libgconf2-ruby libcairo-ruby libatk1-ruby libglib2-ruby libglade2-ruby
  libpango1-ruby libgdk-pixbuf2-ruby librexml-ruby libcairo-ruby1.8
  libgtk2-ruby
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
shoaibi@saber-rider:~/lucent$ cd ltmodem-2.6-alk-8/
shoaibi@saber-rider:~/lucent/ltmodem-2.6-alk-8$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/shoaibi/lucent/ltmodem-2.6-alk-8 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /home/shoaibi/lucent/ltmodem-2.6-alk-8/lt_modem.o
/home/shoaibi/lucent/ltmodem-2.6-alk-8/lt_modem.c:123: error: expected ‘)’ before string constant
/home/shoaibi/lucent/ltmodem-2.6-alk-8/lt_modem.c:125: error: expected ‘)’ before string constant
/home/shoaibi/lucent/ltmodem-2.6-alk-8/lt_modem.c:130: error: expected ‘)’ before string constant
make[2]: *** [/home/shoaibi/lucent/ltmodem-2.6-alk-8/lt_modem.o] Error 1
make[1]: *** [_module_/home/shoaibi/lucent/ltmodem-2.6-alk-8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [module] Error 2
shoaibi@saber-rider:~/lucent/ltmodem-2.6-alk-8$ 
```

---

### Post by shoaibi on 2007-02-22
Okay i have got it this far:
[http://www.heby.de/ltmodem](http://www.heby.de/ltmodem)
how to identify which one is mine?

---

