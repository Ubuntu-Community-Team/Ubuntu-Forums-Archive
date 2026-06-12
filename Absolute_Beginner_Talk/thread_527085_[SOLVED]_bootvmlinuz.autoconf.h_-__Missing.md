---
title: "[SOLVED] /boot/vmlinuz.autoconf.h -  Missing"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by percy_vere_uk on 2007-08-16
Hi

I have installed both feisty 64 bit version and build essentials from the distribution disc and  have for some time now been trying to get an Intel 536EP modem working. From reading other posts I know that there have been a lot of problems with this issue. However I want to try to learn as much about the system as I can so I have been working through the scripts, but I have now reached a plateau. The problem is that I do not have the files    /boot/vmlinuz.autoconf.h  or  /boot/vmlinuz.version.h    and I cannot find any information on what these files are or how they are created. 

So any help please would be appreciated!!!

---

### Post by jamvegan on 2007-08-16
Those are kernel header files.  They can be found in the following directory:

/usr/src/linux-headers-`uname -r`/include/linux/

The files are simply called autoconf.h and version.h in this directory.  If you are running a script that looks for them in the /boot directory, you can copy them there, with the appropriate names, for instance:

sudo cp /usr/src/linux-headers-`uname -r`/include/linux/autoconf.h /boot/vmlinuz.autoconf.h

---

### Post by percy_vere_uk on 2007-08-17
jamvegan

Thank you for your help on this, that has worked just fine. I shall now be able to get a bit further.

percy

---

