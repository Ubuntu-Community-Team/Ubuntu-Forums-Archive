---
title: "Alsa / Compile"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Pirate on 2006-11-12
hi,
i just want to install alsa drivers for my sound card sb live ext. 24 bit
i tried to install like website of alsa said but i got problem while compiling 
        bunzip2 alsa-driver-xxx
        tar -xf alsa-driver-xxx
        cd alsa-driver-xxx
        ./configure --with-cards=ca0106 --with-sequencer=yes
its all ok till here than
        make
i got 

include/linux/pci.h:496: error: expected identifier or &#8216;(&#8217; before numeric constant
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.9rc4a/acore/hpetimer.o] Error 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.9rc4a/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.9rc4a] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [compile] Error 2



so what should i do ?
nobody has an idea?

---

