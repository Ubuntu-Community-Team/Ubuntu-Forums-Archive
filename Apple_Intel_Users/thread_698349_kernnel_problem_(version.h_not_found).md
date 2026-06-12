---
title: "kernnel problem (version.h not found)"
date: 2008-02-16
forum: Apple Intel Users
---

### Post by angel_pirate2006 on 2008-02-16
**HI everyone!!**
 

Yesterday I wanted to install manually a sound driver for  Intel Corporation 82801H model so I made the following commands:

 wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16rc1.tar.bz2)
tar xvpjf alsa-driver-1.0.15rc1.tar.bz2
cd alsa-driver-1.0.15rc1
./configure --with-cards=hda-intel

So everything was going allright but at the last command I had an error and it showed this:
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

I tried update, upgrade, dist-upgrade but it didn't help 
Do you know what am I supposed to do?

Thanks for replying

---

### Post by zanak on 2008-02-16
you have to install linux headers
try :

sudo apt-get build-essential kernel-package linux-kernel-headers

---

### Post by angel_pirate2006 on 2008-02-16
hey man I just tried it but it cannot understand build essential

Thanks for helping

---

### Post by zanak on 2008-02-16
sorry man i forgot the install so try again  with :

 sudo apt-get install build-essential kernel-package linux-headers*

---

### Post by angel_pirate2006 on 2008-02-16
thank you. I used the "sudo apt-get install linux-headers-$(uname -r)" instead and it worked, now I have to do the make command and it gives me this error

aggelos@aggelos-laptop:~/alsa-driver-1.0.15rc1$ make
make dep
make[1]: Entering directory `/home/aggelos/alsa-driver-1.0.15rc1'
make[2]: Entering directory `/home/aggelos/alsa-driver-1.0.15rc1/acore'
copying file alsa-kernel/core/rawmidi.c
/home/aggelos/alsa-driver-1.0.15rc1/utils/patch-alsa: 24: patch: not found
make[2]: *** [rawmidi.c] Error 1
make[2]: Leaving directory `/home/aggelos/alsa-driver-1.0.15rc1/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/aggelos/alsa-driver-1.0.15rc1'
make: *** [include/sndversions.h] Error 2

thanks a lot for your advice

---

### Post by zanak on 2008-02-16
ok it seems that you need patch app:
so do that :
sudo apt-get install patch

hope it helps !

---

### Post by angel_pirate2006 on 2008-02-16
you are the greatest man 
**I realllllllllly love you **

---

### Post by zanak on 2008-02-16
you r welcome ;)

---

### Post by cyberdork33 on 2008-02-16
there is also a newer release of alsa out... You shouldn't have to patch. 1.0.16

---

