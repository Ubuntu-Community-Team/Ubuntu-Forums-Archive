---
title: "56K Lucent Modem [URGENT]"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-24
i am following: 
[http://doc.gwos.org/index.php/PCI_Lucent_winmodem](http://doc.gwos.org/index.php/PCI_Lucent_winmodem)

and i get this 


```

shoaibi@shoaibi-desktop:~$ mkdir ~/lucent
shoaibi@shoaibi-desktop:~$ wget http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-8.tar.bz2
--21:52:23-- http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-8.tar.bz2
=> `ltmodem-2.6-alk-8.tar.bz2'
Connecting to 172.30.10.10:3128... connected.
Proxy request sent, awaiting response... 200 OK
Length: 436,392 (426K) [application/x-bzip2]

100%[====================================>] 436,392 --.--K/s

21:52:24 (2.88 MB/s) - `ltmodem-2.6-alk-8.tar.bz2' saved [436392/436392]

shoaibi@shoaibi-desktop:~$ cd ~/lucent
shoaibi@shoaibi-desktop:~/lucent$ cd
shoaibi@shoaibi-desktop:~$ ls
Desktop Examples ltmodem-2.6-alk-8.tar.bz2 lucent
shoaibi@shoaibi-desktop:~$ mv ltmodem-2.6-alk-8.tar.bz2 /home/shoaibi/lucent/
shoaibi@shoaibi-desktop:~$ cd lucent/
shoaibi@shoaibi-desktop:~/lucent$ ls
ltmodem-2.6-alk-8.tar.bz2
shoaibi@shoaibi-desktop:~/lucent$ tar jxf ltmodem-2.6-alk-8.tar.bz2
shoaibi@shoaibi-desktop:~/lucent$ ls
ltmodem-2.6-alk-8 ltmodem-2.6-alk-8.tar.bz2
shoaibi@shoaibi-desktop:~/lucent$ sudo apt-get install build-essential linux-headers-`uname -r` wvdial
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.17-10-generic is already the newest version.
wvdial is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 146 not upgraded.
shoaibi@shoaibi-desktop:~/lucent$ ls
ltmodem-2.6-alk-8 ltmodem-2.6-alk-8.tar.bz2
shoaibi@shoaibi-desktop:~/lucent$ cd
shoaibi@shoaibi-desktop:~$ cd ~/lucent/ltmodem-2.6-alk-8 make
shoaibi@shoaibi-desktop:~/lucent/ltmodem-2.6-alk-8$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/shoaibi/lucent/ltmodem-2.6-alk-8 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/shoaibi/lucent/ltmodem-2.6-alk-8/lt_modem.o
/home/shoaibi/lucent/ltmodem-2.6-alk-8/lt_modem.c:123: error: expected ‘)’ before string constant
/home/shoaibi/lucent/ltmodem-2.6-alk-8/lt_modem.c:125: error: expected ‘)’ before string constant
/home/shoaibi/lucent/ltmodem-2.6-alk-8/lt_modem.c:130: error: expected ‘)’ before string constant
make[2]: *** [/home/shoaibi/lucent/ltmodem-2.6-alk-8/lt_modem.o] Error 1
make[1]: *** [_module_/home/shoaibi/lucent/ltmodem-2.6-alk-8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [module] Error 2

```

---

### Post by siciliancasanova on 2007-03-13
I think you need the build-essential pack so that your **make** command runs correctly

---

### Post by siciliancasanova on 2007-03-13
Or I could look at your entire code instead of the error and see that you already ran the build-essential, lol. 

Bump anyway.

---

