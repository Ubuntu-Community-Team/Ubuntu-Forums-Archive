---
title: "Help!"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Mightyspider on 2007-04-15
Hello i need help with instslling my wireless driver ive got the pro wireless 3945abg build in wireless.

I tried make and install the drive but i get errors when i do that can anybody help me please.

Im very new to ubuntu.

Thanks in advance
Mightyspider

---

### Post by speeves on 2007-04-15
Hi MightySpider,

Can you send the commands that you tried, the package, the version, version of Ubuntu, and the errors that you are receiving?

thanks,
speeves

---

### Post by lamalex on 2007-04-15
what errors do you get, always post as much info to start as possible

---

### Post by Mightyspider on 2007-04-15
ill get the errors for u guys be right back

---

### Post by Mightyspider on 2007-04-15
well im using ubuntu 6.10 kernel 2.6.17-1- generic

i make and make install the ieee80211

now i need to make and make install the ipw3945-1.2.0 and its jsut telling me that permission is denied and im logged in as root.

i can try and do everything i do and coopy it in to a text and post it or is this engouh info?

Thanks
Mightyspider

---

### Post by Mightyspider on 2007-04-15
WELL THIS IS THE COMMAND I TYPED IN AS FOLLOW:

root@ubuntu-laptop:~# cd Desktop

root@ubuntu-laptop:~/Desktop# ls

Folder  wireless

root@ubuntu-laptop:~/Desktop# cd wireless

root@ubuntu-laptop:~/Desktop/wireless# ls

how to install drivers in linx.txt  ipw3945-linux-1.2.0.tgz
ieee80211-1.2.17                    Merge Wireless Driver.txt
ieee80211-1.2.17.tar.gz             patch-2.6.20.6
ieee80211-1.2.17.tar.gz_FILES       patch-2.6.20.6.bz2
ipw3945-linux-1.2.0                 To login as root.txt
root@ubuntu-laptop:~/Desktop/wireless# cd i
ieee80211-1.2.17/              ipw3945-linux-1.2.0/
ieee80211-1.2.17.tar.gz        ipw3945-linux-1.2.0.tgz
ieee80211-1.2.17.tar.gz_FILES/ 

root@ubuntu-laptop:~/Desktop/wireless# cd i
ieee80211-1.2.17/              ipw3945-linux-1.2.0/
ieee80211-1.2.17.tar.gz        ipw3945-linux-1.2.0.tgz
ieee80211-1.2.17.tar.gz_FILES/ 

root@ubuntu-laptop:~/Desktop/wireless# cd ieee80211-1.2.17

root@ubuntu-laptop:~/Desktop/wireless/ieee80211-1.2.17# ls

CHANGES                     ieee80211_crypt_tkip.mod.c  ieee80211_module.o.lst
compat.h                    ieee80211_crypt_tkip.mod.o  ieee80211.o
GIT_SHA1                    ieee80211_crypt_tkip.o      ieee80211_rx.c
idvals                      ieee80211_crypt_tkip.o.lst  ieee80211_rx.o
ieee80211_crypt.c           ieee80211_crypt_wep.c       ieee80211_rx.o.lst
ieee80211_crypt_ccmp.c      ieee80211_crypt_wep.ko      ieee80211_tx.c
ieee80211_crypt_ccmp.ko     ieee80211_crypt_wep.mod.c   ieee80211_tx.o
ieee80211_crypt_ccmp.mod.c  ieee80211_crypt_wep.mod.o   ieee80211_tx.o.lst
ieee80211_crypt_ccmp.mod.o  ieee80211_crypt_wep.o       ieee80211_wx.c
ieee80211_crypt_ccmp.o      ieee80211_crypt_wep.o.lst   ieee80211_wx.o
ieee80211_crypt_ccmp.o.lst  ieee80211_geo.c             ieee80211_wx.o.lst
ieee80211_crypt.ko          ieee80211_geo.o             INSTALL
ieee80211_crypt.mod.c       ieee80211_geo.o.lst         in-tree
ieee80211_crypt.mod.o       ieee80211.ko                LICENSE
ieee80211_crypt.o           ieee80211.mod.c             Makefile
ieee80211_crypt.o.lst       ieee80211.mod.o             Modules.symvers
ieee80211_crypt_tkip.c      ieee80211_module.c          net
ieee80211_crypt_tkip.ko     ieee80211_module.o          remove-old
root@ubuntu-laptop:~/Desktop/wireless/ieee80211-1.2.17# make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.17-10-generic for ieee80211 components...
/lib/modules/2.6.17-10-generic/net/ieee80211/ieee80211.ko
/lib/modules/2.6.17-10-generic/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.17-10-generic/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.17-10-generic/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.17-10-generic/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.17-10-generic/net/ieee80211/.tmp_versions/ieee80211.mod
/lib/modules/2.6.17-10-generic/net/ieee80211/.tmp_versions/ieee80211_crypt.mod
/lib/modules/2.6.17-10-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_wep.mod
/lib/modules/2.6.17-10-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_ccmp.mod
/lib/modules/2.6.17-10-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_tkip.mod
/lib/modules/2.6.17-10-generic/include/net/ieee80211.h
/lib/modules/2.6.17-10-generic/include/net/ieee80211_crypt.h
/lib/modules/2.6.17-10-generic/include/net/ieee80211_radiotap.h
Above files found.  Remove? [y],n y

make -C /lib/modules/2.6.17-10-generic/build M=/root/Desktop/wireless/ieee80211-1.2.17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:17: 
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:18: WARNING: $SHELL not set to bash.
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:19: If you experience build errors, try
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:20: 'make SHELL=/bin/bash'.
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:21: 
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'

root@ubuntu-laptop:~/Desktop/wireless/ieee80211-1.2.17# make install
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
make -C /lib/modules/2.6.17-10-generic/build M=/root/Desktop/wireless/ieee80211-1.2.17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:17: 
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:18: WARNING: $SHELL not set to bash.
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:19: If you experience build errors, try
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:20: 'make SHELL=/bin/bash'.
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:21: 
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
install -d /lib/modules/2.6.17-10-generic/net/ieee80211/
install -m 644 -c ieee80211.ko ieee80211_crypt.ko ieee80211_crypt_wep.ko ieee80211_crypt_ccmp.ko ieee80211_crypt_tkip.ko /lib/modules/2.6.17-10-generic/net/ieee80211/
install -d `echo /lib/modules/2.6.17-10-generic/include | grep "/net\$" || echo /lib/modules/2.6.17-10-generic/include/net`
install -m 644 -c net/ieee80211.h net/ieee80211_crypt.h net/ieee80211_radiotap.h `echo /lib/modules/2.6.17-10-generic/include | grep "/net\$" || echo /lib/modules/2.6.17-10-generic/include/net`
mkdir -p /lib/modules/2.6.17-10-generic/net/ieee80211//.tmp_versions
cd .tmp_versions && install -m 644 -c ieee80211.mod ieee80211_crypt.mod ieee80211_crypt_wep.mod ieee80211_crypt_ccmp.mod ieee80211_crypt_tkip.mod /lib/modules/2.6.17-10-generic/net/ieee80211//.tmp_versions
/sbin/depmod -a 2.6.17-10-generic

root@ubuntu-laptop:~/Desktop/wireless/ieee80211-1.2.17# cd ..

root@ubuntu-laptop:~/Desktop/wireless# ls

how to install drivers in linx.txt  ipw3945-linux-1.2.0.tgz
ieee80211-1.2.17                    Merge Wireless Driver.txt
ieee80211-1.2.17.tar.gz             patch-2.6.20.6
ieee80211-1.2.17.tar.gz_FILES       patch-2.6.20.6.bz2
ipw3945-linux-1.2.0                 To login as root.txt

root@ubuntu-laptop:~/Desktop/wireless# cd ipw3945-linux-1.2.0

root@ubuntu-laptop:~/Desktop/wireless/ipw3945-linux-1.2.0# ls

Install_and_Support_Notes.txt  ipw3945d-1.7.22
ipw3945-1.2.0                  ipw3945-ucode-1.14.2

root@ubuntu-laptop:~/Desktop/wireless/ipw3945-linux-1.2.0# make
make: *** No targets specified and no makefile found.  Stop.

root@ubuntu-laptop:~/Desktop/wireless/ipw3945-linux-1.2.0# cd ipw3945-1.2.0

root@ubuntu-laptop:~/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0# ls

CHANGES  GIT_SHA1  ipw3945.c         ISSUES       LICENSE.GPL  README.ipw3945
dvals    INSTALL   ipw3945_daemon.h  LICENSE      load         snapshot
FILES    in-tree   ipw3945.h         LICENSE.BSD  Makefile     unload

root@ubuntu-laptop:~/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0# mkae
bash: mkae: command not found

root@ubuntu-laptop:~/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0# make
make: execvp: /root/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0/snapshot/find_ieee80211: Permission denied
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
make: execvp: /root/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0/snapshot/check_ieee80211_compat: Permission denied
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e  Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1
root@ubuntu-laptop:~/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0# make install
make: execvp: /root/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0/snapshot/find_ieee80211: Permission denied
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
make: execvp: /root/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0/snapshot/check_ieee80211_compat: Permission denied
install -d /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/
install -m 644 -c ipw3945.ko /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/
install: cannot stat `ipw3945.ko': No such file or directory
make: *** [install] Error 1
root@ubuntu-laptop:~/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0#

---

### Post by lamalex on 2007-04-15
did you try making the intel drivers before making the ieee80211 ones? there's an error in there about that. try doing a ```
make uninstall
``` in the ieee80211 folder and then installing the intel?

---

### Post by Mightyspider on 2007-04-16
oh ok but how do i install the intel driver?

---

### Post by Mightyspider on 2007-04-17
Any other suggestions? Please im having magor problems with installing my wireless driver

---

### Post by 00arthuryu on 2007-04-17
you could always hope for the best with the new 7.04 distro coming out in a couple of days, apparently that has good wireless compatibility but i can't promise anything as i too am a newbie :KS

---

### Post by Mightyspider on 2007-04-17
cool i will try it out aswell

Thanks

---

