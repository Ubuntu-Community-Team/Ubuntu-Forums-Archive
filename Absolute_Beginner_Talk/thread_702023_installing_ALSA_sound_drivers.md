---
title: "installing ALSA sound drivers"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by elchico04 on 2008-02-19
I am trying to install the drivers for my HDA Mystique 7.1 sound card. In the device manager it is telling me that I have the CM8738 chipset when I am pretty sure that it has the CMI8768+ chipset. Anywho, first i do ./configure and that works just fine but then when run the command "make" I get a bunch of errors and it stops.

> make[4]: *** [/home/alantor08/Desktop/audio/pci/asihpi/hpimod.o] Error 1
make[3]: *** [/home/alantor08/Desktop/audio/pci/asihpi] Error 2
make[2]: *** [/home/alantor08/Desktop/audio/pci] Error 2
make[1]: *** [_module_/home/alantor08/Desktop/audio] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-51-amd64-generic'
make: *** [compile] Error 2


Am I missing dependencies or something? I have no idea what these errors mean.

---

### Post by spiderbatdad on 2008-02-20
Hard to know what you've done so far. Have you removed anything, like alsa-base?
You many only need :```
sudo aptitude install linux-backports-modules-generic
depmod -a
``` But if you need to rebuild alsa, check out the appropriate section of this guide.[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

