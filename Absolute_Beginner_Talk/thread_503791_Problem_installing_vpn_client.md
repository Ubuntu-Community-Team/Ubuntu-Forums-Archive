---
title: "Problem installing vpn client"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Pebbles on 2007-07-18
Hi, 

I am trying to install vpn client, but I keep getting this error message:

Making module
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/andrea/Programme_Downloads/Vpnclient modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/andrea/Programme_Downloads/Vpnclient/linuxcniapi.o
/home/andrea/Programme_Downloads/Vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/andrea/Programme_Downloads/Vpnclient/linuxcniapi.o] Fehler 1
make[1]: *** [_module_/home/andrea/Programme_Downloads/Vpnclient] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Fehler 2
Failed to make module "cisco_ipsec.ko".

I already applied the patch (vpnclient-linux-2.6.22.diff), but it doesn't help (although there were three CC [M] .. lines before, compared to only one now)

Does anybody have any ideas?

Thanks!

---

### Post by cmnorton on 2007-07-18
Do you have a strong requirement for this application that cannot be satisfied with, for example, pptpconfig?

---

