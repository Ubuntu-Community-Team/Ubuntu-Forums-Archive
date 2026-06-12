---
title: "Install drivers from tarball"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by bezzer on 2005-09-20
I have a usb modem.  It has a drivers disk with a tarball for linux drivers.  I did tar xvzf and because there was a makefile (and the readme said to) I did make.  I got an error message and I think the make stopped.  

Before I copy the error message, is this likely to be something to do with kernel headers?  I don't really understand what these are or how they work.  If so, please can someone give me some instructions, if not, I'll try again and copy down the error message.

Thanks
D

---

### Post by mlomker on 2005-09-20
Yeah, you pretty much need headers and the compiler to build anything.  Start with this:

```

sudo apt-get install build-essential
sudo apt-get install linux-headers-$(uname -r)

```

---

### Post by bezzer on 2005-09-20
OK so installed build essential through synaptic, tried to install linux-headers using apt-get but it wouldn't, so installed the appropriate one from synaptic (or should I have installed all three?

This is the make log it's doing

```
gcc -O2 -fomit-frame-pointer -fno-strict-aliasing -pipe -fno-strength-reduce -DCPU=686 -march=i686  -DMODULE -D__KERNEL__ -DLINUX  -I/lib/modules/`uname -r`/build/include -c usbsndcm.c -o usbsndcm.o
In file included from /lib/modules/2.6.10-5-386/build/include/linux/irq.h:21,
                 from /lib/modules/2.6.10-5-386/build/include/asm/hardirq.h:6,
                 from /lib/modules/2.6.10-5-386/build/include/linux/hardirq.h:6,                 from /lib/modules/2.6.10-5-386/build/include/linux/interrupt.h:11,
                 from /lib/modules/2.6.10-5-386/build/include/linux/usb.h:15,
                 from hasbani.h:29,
                 from usbsndcm.c:20:
/lib/modules/2.6.10-5-386/build/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /lib/modules/2.6.10-5-386/build/include/asm/hardirq.h:6,
                 from /lib/modules/2.6.10-5-386/build/include/linux/hardirq.h:6,                 from /lib/modules/2.6.10-5-386/build/include/linux/interrupt.h:11,
                 from /lib/modules/2.6.10-5-386/build/include/linux/usb.h:15,
                 from hasbani.h:29,
                 from usbsndcm.c:20:
/lib/modules/2.6.10-5-386/build/include/linux/irq.h:71: error: `NR_IRQS' undeclared here (not in a function)
In file included from /lib/modules/2.6.10-5-386/build/include/linux/irq.h:73,
                 from /lib/modules/2.6.10-5-386/build/include/asm/hardirq.h:6,
                 from /lib/modules/2.6.10-5-386/build/include/linux/hardirq.h:6,                 from /lib/modules/2.6.10-5-386/build/include/linux/interrupt.h:11,
                 from /lib/modules/2.6.10-5-386/build/include/linux/usb.h:15,
                 from hasbani.h:29,
                 from usbsndcm.c:20:
/lib/modules/2.6.10-5-386/build/include/asm/hw_irq.h:28: error: `NR_IRQ_VECTORS' undeclared here (not in a function)
/lib/modules/2.6.10-5-386/build/include/asm/hw_irq.h:32: error: `NR_IRQS' undeclared here (not in a function)
In file included from /lib/modules/2.6.10-5-386/build/include/asm/hardirq.h:6,
                 from /lib/modules/2.6.10-5-386/build/include/linux/hardirq.h:6,                 from /lib/modules/2.6.10-5-386/build/include/linux/interrupt.h:11,
                 from /lib/modules/2.6.10-5-386/build/include/linux/usb.h:15,
                 from hasbani.h:29,
                 from usbsndcm.c:20:
/lib/modules/2.6.10-5-386/build/include/linux/irq.h:78: error: `NR_IRQS' undeclared here (not in a function)
make: *** [usbsndcm.o] Error 1
```

Any ideas?  it all means nothing to me.

Thanks
Dave

---

### Post by mlomker on 2005-09-20
Did you install the headers that match the output of **uname -r**? 

If so, then I'm not sure.

---

### Post by bezzer on 2005-09-20
Have definitely installed the headers that came back from linux-header-$(uname -r).

If I can't get on the net it makes Ubuntu pretty useless to me... :(

D

---

