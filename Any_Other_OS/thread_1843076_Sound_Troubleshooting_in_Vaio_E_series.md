---
title: "Sound Troubleshooting in Vaio E series"
date: 2011-09-12
forum: Any Other OS
---

### Post by wgarciamachmar on 2011-09-12
I had some issues with my sound driver in ubuntu natty (Mint 11 actually). The speaker was working, but no mic or headphone jack.

My specs are:
```
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Sony Corporation Device 908a
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at d2600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

```

I tried compiling alsa from scratch and then I lost all sound.

Then, I used the Comprehensive Troubleshooting Guide and it was working fine until step 4. So, when I enter ```
sudo module-assistant a-i   alsa-source
``` I get to a 48% success and then, it crashes.

The erro lines are as follows.

```
/usr/src/modules/alsa-driver/include/linux/pci_ids.h:2:58: fatal error:     
 &#9474; @CONFIG_SND_KERNELSRC@/include/linux/pci_ids.h: No existe el fichero o el   
 &#9474; directorio                                                                  
 &#9474; compilation terminated.                                                     
 &#9474; make[5]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1        
 &#9474; make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2                   
 &#9474; make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
 &#9474; make[3]: se sale del directorio «/usr/src/linux-headers-2.6.38-11-generic»  
 &#9474; make[2]: *** [compile] Error 2                                              
 &#9474; make[2]: se sale del directorio «/usr/src/modules/alsa-driver»              
 &#9474; make[1]: *** [build-stamp] Error 2                                          
 &#9474; make[1]: se sale del directorio «/usr/src/modules/alsa-driver»              
 &#9474; make: *** [kdist_image] Error 2              

```

Of course, there is a bunch of lines before, but nothing seems to go wrong up until these lines.

---

### Post by Perfect Storm on 2011-09-12
Moved to Other OS/Distro Talk.

---

