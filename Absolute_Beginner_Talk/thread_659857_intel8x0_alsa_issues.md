---
title: "intel8x0 alsa issues"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by mlorsung on 2008-01-06
so the sound on my intel8x0 soundcard went out for no apparent reason after having worked for months--I followed the instructions in the sound troubleshooting guide--the computer detects the card, but the drivers dont seem to want to install.  I tried using the automatic method, as well as recompiling them manually.  Below is the error I get--Im really at my wits end, if anyone can help, PLEASE PLEASE do

thanks,
Michael
```
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/usr/src/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o
In file included from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition of ‘jiffies_to_msecs’
include/linux/jiffies.h:268: error: previous definition of ‘jiffies_to_msecs’ was here
/usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition of ‘msecs_to_jiffies’
include/linux/jiffies.h:290: error: previous definition of ‘msecs_to_jiffies’ was here
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many arguments to function ‘pci_save_state’
/usr/src/modules/alsa-driver/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [compile] Error 2
blacklines@ubuntu:/usr/src/modules/alsa-driver$ sudo make install
find /lib/modules/2.6.20-16-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
make[1]: Entering directory `/usr/src/modules/alsa-driver/acore'
mkdir -p /lib/modules/2.6.20-16-generic/kernel/sound/acore
cp snd-page-alloc.ko snd-pcm.ko snd-timer.ko snd.ko /lib/modules/2.6.20-16-generic/kernel/sound/acore
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
```

---

### Post by mlorsung on 2008-01-06
bump?  please?

---

### Post by mlorsung on 2008-01-09
bump again???

---

