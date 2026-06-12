---
title: "sound on ibm 770"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by MkfIbK7a on 2007-01-09
ok so my mother has an ibm 770 and i put xubuntu on it but the sound doesnt work](*,) 

does anyone know of a good howto with clear steps or did anyone else deal with this problem ever?

Thnx

---

### Post by deadgobby on 2007-01-09
The Think Pad 770 uses the Crystal 4236 chip set. 
    CONFIG_SOUND=m
    CONFIG_SOUND_OSS=m
    CONFIG_SOUND_CS4232=m
It is necessary to compile the sound drivers as modules, because after every suspend the driver gets broken. It has to be restarted, which is only possible, when the sound modules are reloaded.

In order to load the modules automatically on demand, Add the following lines to the file /etc/conf.modules

    alias char-major-14 cs4232
    options cs4232 io=0x530 irq=5 dma=1 dma2=0

(the right way to do this on an Debian system is to add these lines to the file /etc/modutils/aliases or create a file - for example sound in /etc/modutils - and then execute update-modules)

With the help of the apmd daemon it is easy to automatically unload the sound driver (when it was loaded with kmod or kerneld): Simply put the file sound in the directory /etc/apm/suspend.d and make it executable. 

Taken from link
[http://mathphys.fsk.uni-heidelberg.de/~mfluch/tp770.html](http://mathphys.fsk.uni-heidelberg.de/~mfluch/tp770.html)

Gobby

---

### Post by MkfIbK7a on 2007-01-09
thanks gobby ill try that.:D

---

### Post by MkfIbK7a on 2007-01-14
sorry gobby it didnt work:(

anyone else this is getting desperate!!

---

### Post by MkfIbK7a on 2007-01-14
help someone plz?

---

