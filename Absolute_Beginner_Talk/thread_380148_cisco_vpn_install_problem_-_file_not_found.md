---
title: "cisco vpn install problem - file not found"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by martinjcole on 2007-03-09
Hi,

I am trying to install cisco vpn, and encountering some issues, I have tried quite a few searches for information, but my problem does not appear in anything I have found yet.

The specific issue is during the execution of vpn_install

--------------------------------------------------------------------------------
Making module
make -C /usr/src/linux-headers-2.6.20-9 SUBDIRS=/home/mcole/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-9'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.20-9/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/mcole/Desktop/vpnclient/linuxcniapi.o
/home/mcole/Desktop/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/mcole/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/mcole/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-9'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
----------------------------------------------------------------------

Any thoughts ?


Martin

running on a dell d610, using feisty.

---

### Post by martinjcole on 2007-03-09
I got one step closer.

I created an empty config.h file in the includes/linux/ folder, as per another post to a similar but different error, and was able to get further, however I wonder if the installer is assuming information in the "missing" file.

Hmm still rather stuck...

Martin

---

### Post by ipguru99 on 2007-03-30
For some reason, there were two things in feisty I needed to do to get this running

I also got the dreaded config.h not found thing...

The first web site was:

[http://www.tuxx-home.at/archives/2006/12/07/T09_36_48/](http://www.tuxx-home.at/archives/2006/12/07/T09_36_48/)

It talks about patching 2.6.19.. but I used it on 2.6.20-13 today.. 

Then:
[http://www.linuxforums.org/forum/linux-networking/44372-cisco-vpn-client-compile-error.html](http://www.linuxforums.org/forum/linux-networking/44372-cisco-vpn-client-compile-error.html)

This talks about replacing 'stb->stamp' with stb->tstamp' in the vpnclient/linuxcniapi.c file

After that.. it worked!  All of my pcf files load just like they used to!

---

