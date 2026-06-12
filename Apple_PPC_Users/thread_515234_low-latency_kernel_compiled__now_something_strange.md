---
title: "low-latency kernel compiled // now something strange"
date: 2007-08-01
forum: Apple PPC Users
---

### Post by jaskah on 2007-08-01
i just compiled a low latency kernel for my g4 titanium powerbook with the following kernel:
linux-2.6.19.7.tar.bz2
after rebooting everything seems to be working great **EXCEPT** for a small light which flickers at the base of my screen whenever the hard drive seems to be working. under normal circumstances (vanilla install) this light only goes on when the computer is in sleep mode.
is there any way to disable this and stop the flickering?
thanks for any help!

---

### Post by Tommy on 2007-08-03
> **jaskah said:**
> i just compiled a low latency kernel for my g4 titanium powerbook with the following kernel:
linux-2.6.19.7.tar.bz2
after rebooting everything seems to be working great **EXCEPT** for a small light which flickers at the base of my screen whenever the hard drive seems to be working. under normal circumstances (vanilla install) this light only goes on when the computer is in sleep mode.
is there any way to disable this and stop the flickering?


I just happened to notice this on the Debian-PowerPC mailing list. It's entirely benign, but I can understand how it might be disturbing. Here's the message I saw:

[http://lists.debian.org/debian-powerpc/2007/07/msg00132.html](http://lists.debian.org/debian-powerpc/2007/07/msg00132.html)

> as of linux-image-2.6.22-1-powerpc, CONFIG_ADB_PMU_LED is enabled, so this can be enabled at runtime by writing 'ide-disk' into class/leds/pmu-front-led/trigger, e.g. via sysfsutil's /etc/sysfs.conf[FONT=Tahoma,Sans,Arial,Helvetica,sans-serif]

So you can either re-compile with the CONFIG_ADB_PMU_LED disabled OR you can put a different trigger into the configuration file.

:)
[/FONT]

---

### Post by stmiller on 2007-08-03
Uncheck this option:

Device Drivers>Machintosh device drivers> [ ] Use front LED as IDE LED by default

---

### Post by jaskah on 2007-08-16
hi
thanks for your reply.

> **stmiller said:**
> Uncheck this option:
Device Drivers>Machintosh device drivers> [ ] Use front LED as IDE LED by default

where do i uncheck this?

thanks again!

---

### Post by jaskah on 2007-08-16
hi
thanks for your reply

> **Tommy said:**
> I just happened to notice this on the Debian-PowerPC mailing list. It's entirely benign, but I can understand how it might be disturbing. Here's the message I saw:

[http://lists.debian.org/debian-powerpc/2007/07/msg00132.html](http://lists.debian.org/debian-powerpc/2007/07/msg00132.html)

[FONT=Tahoma,Sans,Arial,Helvetica,sans-serif]

So you can either re-compile with the CONFIG_ADB_PMU_LED disabled OR you can put a different trigger into the configuration file.

FYI, as of linux-image-2.6.22-1-powerpc, CONFIG_ADB_PMU_LED is enabled,
so this can be enabled at runtime by writing 'ide-disk' into
class/leds/pmu-front-led/trigger, e.g. via sysfsutil's /etc/sysfs.conf.

[/FONT]

i´m somewhat new to linux. how can i do this? i don´t have the file /etc/sysfs.conf in my system.

---

### Post by stmiller on 2007-08-17
> where do i uncheck this?

It's an option when you compile your kernel. (During 'make menuconfig')

Unfortunately you will have to recompile the kernel to turn this on or off. The PowerPCFAQs has steps if you need help.

EDIT:

Or 
```

sudo apt-get install sysfsutils

```
and see if that results in a /etc/sysfs.conf

---

### Post by jaskah on 2007-08-17
thanks again for your help!
i will give these options a try.

---

