---
title: "Please Compile This Module For Me..."
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by hellmet on 2006-05-07
Hello people..
 I am havin some tuff time trying to compile this thing.
 I need Linux_source for this..which I don't have.
its a 35 MB file..that'll take ages to download for me.

[B]I am Presently on Breezy Badger kernel 2.6x
I need you guys to Compile the Kernel Module for me
There is the make file that must be edited acc. to your kernel
Please do it..I beg of u guys...[/B]

---

### Post by hw-tph on 2006-05-07
The driver you posted is for Linux 2.4.18. Not only is it old, but if you do run a Linux 2.4 system you should really use a later revision (the current one is 2.4.33). Ubuntu ships with 2.6 series kernels (2.6.12 I think in Breezy).

That shouldn't be of any great matter though since the driver provides support for Realtek 8139C+ cards, which is in the standard Ubuntu kernel. This means you should not need this driv.er

Why exactly do you want this particular driver (as opposed to the one that ships with the distribution)?


Håkan

---

### Post by hellmet on 2006-05-07
I need it for RTL8139D NIC.
It is not supported in Ubuntu.
But a few ppl have got it working,
by addin a line in it.
I did it, but I think I got the wrong Kernel version

---

### Post by towsonu2003 on 2006-05-08
:confused: :confused: I thought I added my comments here. weird... 

anyway. I tried this, but couldn;t do. In makefile, I changed the lines like this: 
```
CC=gcc**-3.4**
MODCFLAGS := -O6 -Wall -DCONFIG_KERNELD -DMODULE -D__KERNEL__ -DLINUX
NEW_INCLUDE_PATH=-I /usr/src/**linux**/include/

8139too.o:      8139too.c /usr/include/linux/version.h
                $(CC) $(MODCFLAGS) $(NEW_INCLUDE_PATH) -c 8139too.c

```after making sure /usr/src/linux points to correct place. check with ls -l /usr/src the symlink should go to linux-headers-`uname -r` -> uname -r will give your current kernel version in terminal. For gcc-3.4, you need to install it thru repos first... 

here are the errors for ppl who know this stuff:
```
~$ make


gcc-3.4 -O6 -Wall -DCONFIG_KERNELD -DMODULE -D__KERNEL__ -DLINUX  -I /usr/src/linux/include/ -c 8139too.c
In file included from /usr/src/linux/include/asm/processor.h:18,
                 from /usr/src/linux/include/asm/thread_info.h:17,
                 from /usr/src/linux/include/linux/thread_info.h:21,
                 from /usr/src/linux/include/linux/spinlock.h:12,
                 from /usr/src/linux/include/linux/capability.h:45,
                 from /usr/src/linux/include/linux/sched.h:7,
                 from /usr/src/linux/include/linux/module.h:10,
                 from 8139too.c:107:
/usr/src/linux/include/asm/system.h: In function `__set_64bit_var':
/usr/src/linux/include/asm/system.h:193: warning: dereferencing type-punned pointer will break strict-aliasing rules
/usr/src/linux/include/asm/system.h:193: warning: dereferencing type-punned pointer will break strict-aliasing rules
In file included from /usr/src/linux/include/linux/irq.h:21,
                 from /usr/src/linux/include/asm/hardirq.h:6,
                 from /usr/src/linux/include/linux/hardirq.h:6,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from /usr/src/linux/include/asm/highmem.h:24,
                 from /usr/src/linux/include/linux/highmem.h:12,
                 from /usr/src/linux/include/linux/skbuff.h:27,
                 from /usr/src/linux/include/linux/if_ether.h:107,
                 from /usr/src/linux/include/linux/netdevice.h:29,
                 from 8139too.c:112:
/usr/src/linux/include/asm/irq.h:16:25: irq_vectors.h: No such file or directoryIn file included from /usr/src/linux/include/asm/hardirq.h:6,
                 from /usr/src/linux/include/linux/hardirq.h:6,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from /usr/src/linux/include/asm/highmem.h:24,
                 from /usr/src/linux/include/linux/highmem.h:12,
                 from /usr/src/linux/include/linux/skbuff.h:27,
                 from /usr/src/linux/include/linux/if_ether.h:107,
                 from /usr/src/linux/include/linux/netdevice.h:29,
                 from 8139too.c:112:
/usr/src/linux/include/linux/irq.h: At top level:
/usr/src/linux/include/linux/irq.h:72: error: `NR_IRQS' undeclared here (not in a function)
In file included from /usr/src/linux/include/linux/irq.h:74,
                 from /usr/src/linux/include/asm/hardirq.h:6,
                 from /usr/src/linux/include/linux/hardirq.h:6,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from /usr/src/linux/include/asm/highmem.h:24,
                 from /usr/src/linux/include/linux/highmem.h:12,
                 from /usr/src/linux/include/linux/skbuff.h:27,
                 from /usr/src/linux/include/linux/if_ether.h:107,
                 from /usr/src/linux/include/linux/netdevice.h:29,
                 from 8139too.c:112:
/usr/src/linux/include/asm/hw_irq.h:28: error: `NR_IRQ_VECTORS' undeclared here (not in a function)
8139too.c: In function `rtl8139_init_board':
8139too.c:813: warning: implicit declaration of function `init_etherdev'
8139too.c:813: warning: assignment makes pointer from integer without a cast
8139too.c:931: error: structure has no member named `slot_name'
8139too.c:932: error: structure has no member named `slot_name'
8139too.c: In function `rtl8139_init_one':
8139too.c:1053: error: structure has no member named `driver_data'
8139too.c: In function `rtl8139_remove_one':
8139too.c:1136: error: structure has no member named `driver_data'
8139too.c:1164: error: structure has no member named `driver_data'
8139too.c: In function `rtl8139_open':
8139too.c:1382: warning: passing arg 2 of `request_irq' from incompatible pointer type
8139too.c: In function `rtl8139CP_open':
8139too.c:1570: warning: passing arg 2 of `request_irq' from incompatible pointer type
8139too.c: In function `rtl8139_thread':
8139too.c:1926: error: too few arguments to function `daemonize'
8139too.c:1927: error: structure has no member named `sigmask_lock'
8139too.c:1929: error: too many arguments to function `recalc_sigpending'
8139too.c:1930: error: structure has no member named `sigmask_lock'
8139too.c: In function `rtl8139_set_rx_mode':
8139too.c:2994: warning: passing arg 2 of `set_bit' from incompatible pointer type
8139too.c: In function `rtl8139_suspend':
8139too.c:3019: error: structure has no member named `driver_data'
8139too.c: In function `rtl8139_resume':
8139too.c:3051: error: structure has no member named `driver_data'
make: *** [8139too.o] Error 1

```

PS. Don't forget to file a bug to launchpad to tell devels that your card isn't supported...

---

### Post by hw-tph on 2006-05-08
I don't know about the 2.6.12 kernel included by default in Ubuntu but current 2.6 series kernels have support for the 8139d in the 8139too driver.


Håkan

---

