---
title: "kernel error?"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-12-05
Hi all

Trying to install a driver for an ethernet card, I got this message

```
*****************************
 sc92031.o built for 2.6.15-26-386
   SMP Disabled
*****************************

In file included from /lib/modules/2.6.15-26-386/build/include/linux/irq.h:22,
                 from /lib/modules/2.6.15-26-386/build/include/asm/hardirq.h:6,
                 from /lib/modules/2.6.15-26-386/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.15-26-386/build/include/linux/interrupt.h:11,
                 from /lib/modules/2.6.15-26-386/build/include/linux/rcuref.h:36,
                 from /lib/modules/2.6.15-26-386/build/include/linux/fs.h:12,
                 from /lib/modules/2.6.15-26-386/build/include/linux/mm.h:15,
                 from /lib/modules/2.6.15-26-386/build/include/asm/pci.h:7,
                 from /lib/modules/2.6.15-26-386/build/include/linux/pci.h:612,
                 from sc92031.c:19:
/lib/modules/2.6.15-26-386/build/include/asm/irq.h:16:25: error: irq_vectors.h: No such file or directory
In file included from /lib/modules/2.6.15-26-386/build/include/asm/hardirq.h:6,
                 from /lib/modules/2.6.15-26-386/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.15-26-386/build/include/linux/interrupt.h:11,
                 from /lib/modules/2.6.15-26-386/build/include/linux/rcuref.h:36,
                 from /lib/modules/2.6.15-26-386/build/include/linux/fs.h:12,
                 from /lib/modules/2.6.15-26-386/build/include/linux/mm.h:15,
                 from /lib/modules/2.6.15-26-386/build/include/asm/pci.h:7,
                 from /lib/modules/2.6.15-26-386/build/include/linux/pci.h:612,
                 from sc92031.c:19:
/lib/modules/2.6.15-26-386/build/include/linux/irq.h:85: error: ‘NR_IRQS’ undeclared here (not in a function)
In file included from /lib/modules/2.6.15-26-386/build/include/linux/irq.h:94,
                 from /lib/modules/2.6.15-26-386/build/include/asm/hardirq.h:6,
                 from /lib/modules/2.6.15-26-386/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.15-26-386/build/include/linux/interrupt.h:11,
                 from /lib/modules/2.6.15-26-386/build/include/linux/rcuref.h:36,
                 from /lib/modules/2.6.15-26-386/build/include/linux/fs.h:12,
                 from /lib/modules/2.6.15-26-386/build/include/linux/mm.h:15,
                 from /lib/modules/2.6.15-26-386/build/include/asm/pci.h:7,
                 from /lib/modules/2.6.15-26-386/build/include/linux/pci.h:612,
                 from sc92031.c:19:
/lib/modules/2.6.15-26-386/build/include/asm/hw_irq.h:30: error: ‘NR_IRQ_VECTORS’ undeclared here (not in a function)
In file included from /lib/modules/2.6.15-26-386/build/include/linux/if_ether.h:109,
                 from /lib/modules/2.6.15-26-386/build/include/linux/netdevice.h:29,
                 from sc92031.c:22:
/lib/modules/2.6.15-26-386/build/include/linux/skbuff.h: In function ‘skb_add_data’:
/lib/modules/2.6.15-26-386/build/include/linux/skbuff.h:1128: warning: pointer targets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedness
sc92031.c:103:40: error: missing binary operator before token "("
sc92031.c: In function ‘silan_probe’:
sc92031.c:410: error: ‘struct pci_dev’ has no member named ‘slot_name’
sc92031.c:426: error: ‘struct pci_dev’ has no member named ‘slot_name’
sc92031.c:457: error: ‘struct pci_dev’ has no member named ‘slot_name’
sc92031.c:464: error: ‘struct pci_dev’ has no member named ‘slot_name’
sc92031.c: In function ‘silan_open’:
sc92031.c:923: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
sc92031.c: In function ‘silan_ethtool_ioctl’:
sc92031.c:1804: error: ‘struct pci_dev’ has no member named ‘slot_name’
sc92031.c:1814: error: ‘np’ undeclared (first use in this function)
sc92031.c:1814: error: (Each undeclared identifier is reported only once
sc92031.c:1814: error: for each function it appears in.)
sc92031.c:1866:40: error: missing binary operator before token "("
sc92031.c: At top level:
sc92031.c:1976: warning: initialization from incompatible pointer type
sc92031.c: In function ‘silan_init_module’:
sc92031.c:1992: warning: pointer targets in assignment differ in signedness
sc92031.c:1995: warning: pointer targets in assignment differ in signedness
sc92031.c:1998: warning: pointer targets in assignment differ in signedness
sc92031.c:2001: warning: pointer targets in assignment differ in signedness
sc92031.c:2004: warning: pointer targets in assignment differ in signedness
make: *** [sc92031.o] Error 1
```

Is there anyone please who can help me?

Thanks

---

### Post by Dmole on 2007-01-03
I think you are missing some code try reading the install guide to determine if you have all the prerequisites

---

