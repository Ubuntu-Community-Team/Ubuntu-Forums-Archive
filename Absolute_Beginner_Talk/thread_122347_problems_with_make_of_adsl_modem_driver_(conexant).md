---
title: "problems with make of adsl modem driver (conexant)"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by alpy wright on 2006-01-27
I have installed gcc3.4 as directed to compile the driver.  I was told by two different people that I only needed to download the kernel headers to compile the driver.  When I set up a symbolic link to the kernel headers as /usr/src/linux and run the make I get:

root@dell:/# cd CnxADSL-6.1.2.007-PIM-2.6-1.4
root@dell:/CnxADSL-6.1.2.007-PIM-2.6-1.4# make
for n in KernelModule/DpController; \
        do if [ -d $n ]; then make -C $n all || exit; fi; done
for n in KernelModule DownLoadApp; do make -C $n all || exit; done
make[1]: Entering directory `/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make CnxADSL.ko
make[2]: Entering directory `/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make -C /usr/src/linux SUBDIRS=`pwd` modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
make[3]: Makefile: No such file or directory
make[3]: *** No rule to make target `Makefile'.  Stop.
make[3]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[2]: *** [CnxADSL.ko] Error 2
make[2]: Leaving directory `/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make: *** [all] Error 2

I seem to get a lot further by setting up a link (/usr/src/linux) to the kernel source:

root@dell:/CnxADSL-6.1.2.007-PIM-2.6-1.4# cd /usr/src
root@dell:/usr/src# ls
linux  linux-headers-2.6.12-9-386  linux-source-2.6.12  linux-source-2.6.12.tar

'linux' is a symbolic link to the linux headers still (I was told to try this) so I remove it and redirect it to the kernel source:

root@dell:/usr/src# rm linux
root@dell:/usr/src# ln -s /usr/src/linux-source-2.6.12 /usr/src/linux

then 'make' again:

root@dell:/usr/src# cd /CnxADSL-6.1.2.007-PIM-2.6-1.4
root@dell:/CnxADSL-6.1.2.007-PIM-2.6-1.4# make
for n in KernelModule/DpController; \
        do if [ -d $n ]; then make -C $n all || exit; fi; done
for n in KernelModule DownLoadApp; do make -C $n all || exit; done
make[1]: Entering directory `/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make CnxADSL.ko
make[2]: Entering directory `/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make -C /usr/src/linux SUBDIRS=`pwd` modules
make[3]: Entering directory `/usr/src/linux-source-2.6.12'

always get this error (makefile 485 .config) don't know what it is or whether it's important.  Build-essential has been installed:

Makefile:485: .config: No such file or directory

Haven't a clue what this warning is:

  WARNING: Symbol version dump /usr/src/linux-source-2.6.12/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.o
In file included from include/linux/linkage.h:4,
                 from include/linux/kernel.h:11,
                 from /CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/LnxTools.h:39,
                 from /CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.c:34:
include/linux/config.h:4:28: linux/autoconf.h: No such file or directory
In file included from include/asm/thread_info.h:17,
                 from include/linux/thread_info.h:21,
                 from include/linux/spinlock.h:12,
                 from include/linux/seqlock.h:30,
                 from include/linux/time.h:7,
                 from include/linux/skbuff.h:20,
                 from /CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/LnxTools.h:41,
                 from /CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.c:34:
include/asm/processor.h:69: error: `CONFIG_X86_L1_CACHE_SHIFT' undeclared here (not in a function)
include/asm/processor.h:69: error: requested alignment is not a constant
In file included from include/linux/module.h:23,
                 from include/net/sock.h:47,
                 from include/linux/atmdev.h:211,
                 from /CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/CnxADSL.h:37,
                 from /CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.c:42:
include/asm/module.h:58:2: #error unknown processor family
In file included from include/asm/hardirq.h:6,
                 from include/linux/hardirq.h:6,
                 from include/linux/interrupt.h:11,
                 from include/linux/netdevice.h:514,
                 from include/net/sock.h:48,
                 from include/linux/atmdev.h:211,
                 from /CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/CnxADSL.h:37,
                 from /CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.c:42:
include/linux/irq.h:70: error: requested alignment is not a constant
In file included from include/linux/hardirq.h:6,
                 from include/linux/interrupt.h:11,
                 from include/linux/netdevice.h:514,
                 from include/net/sock.h:48,
                 from include/linux/atmdev.h:211,
                 from /CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/CnxADSL.h:37,
                 from /CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.c:42:
include/asm/hardirq.h:13: error: requested alignment is not a constant
In file included from /CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ChipALCdsl.h:37,
                 from /CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/CardMgmt.h:369,
                 from /CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/CnxADSL.h:41,
                 from /CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.c:42:

Now these are different:  maybe i need to recompile the kernel with ATM support:

/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/Version.h:63:2: #error "CONFIG_ATM not defined, you can't use this driver without it"
/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/Version.h:69:2: #error "CONFIG_PPP not defined, you can't use this driver without it"
/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/Version.h:75:2: #error "CONFIG_PPPOATM not defined, you can't use this driver without it"
make[4]: *** [/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.o] Error 1
make[3]: *** [_module_/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule] Error 2
make[3]: Leaving directory `/usr/src/linux-source-2.6.12'
make[2]: *** [CnxADSL.ko] Error 2
make[2]: Leaving directory `/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make: *** [all] Error 2
root@dell:/CnxADSL-6.1.2.007-PIM-2.6-1.4#

I took the latest version of the conexant accessrunner driver that I could find.  I think this is always right.

Can anyone help me?  I just want to get online and ditch windows.  I have managed it before on my own but not with an ADSL modem.

8-[

---

### Post by lanef on 2006-01-27
hi i saw build essential.but you also need linux headers.this should complete
what you're trying to do.linux headers is the kernel source for compiling,unless
you have the source code.use synaptic and your breezy cd.its there


see you later

---

### Post by alpy wright on 2006-01-27
>hi i saw build essential.but you also need linux headers.this should complete
>what you're trying to do.linux headers is the kernel source for compiling,unless
>you have the source code.use synaptic and your breezy cd.its there

I have the linux headers.  I downloaded them you can see where I put them in the terminal capture I showed.  I couldn't see any kernel source or headers on the cd - where may they be?  Anyway I downloaded them.

I can't use synaptic or apt-get because I haven't managed to connect yet the current exercise is to get me connected.

The screen capture shows that the make was going some way into compiling the driver.  

Do I need to make another symbolic link to the linux headers?

I suspect that It was compiling and the errors shown are for different reasons.

This is a new  install all I've done to it is put the kernel code and headers onto it and installed build-essential.  Also gcc-3.4 to enable me to compile the driver.

---

### Post by lanef on 2006-01-28
hi, Im not sure one the link to the headers.i forgot to add the link for compiling
try ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
when i built my modem driver,this was the one of the 2 links i used.
the other was to dev/modem

sorry about that. this should help

---

### Post by benskiedra on 2006-03-04
Hello everybody. I'm also now trying to make my AccessRunner DSL PCi modem working on Ubuntu. It's hard enough for me... I got this error:

[FONT="Courier New"][SIZE="2"]benskis@beno:~$ cd /root/
benskis@beno:/root$ dir
CnxADSL-6.1.2.007-PIM-2.6-1.3  dbootstrap_settings
CnxADSL-6.1.2.007-PIM-2.6-1.4  Desktop
benskis@beno:/root$ cd CnxADSL-6.1.2.007-PIM-2.6-1.4
benskis@beno:/root/CnxADSL-6.1.2.007-PIM-2.6-1.4$ make
for n in KernelModule/DpController; \
        do if [ -d $n ]; then make -C $n all || exit; fi; done
for n in KernelModule DownLoadApp; do make -C $n all || exit; done
make[1]: Entering directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make CnxADSL.ko
make[2]: Entering directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make -C /usr/src/linux SUBDIRS=`pwd` modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[3]: gcc-3.4: Command not found
make[3]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.o
/bin/sh: gcc-3.4: command not found
make[4]: *** [/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.o] Error 127
make[3]: *** [_module_/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[2]: *** [CnxADSL.ko] Error 2
make[2]: Leaving directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make: *** [all] Error 2
benskis@beno:/root/CnxADSL-6.1.2.007-PIM-2.6-1.4$[/SIZE][/FONT]

Where's the source of this error? Am I doing something wrong? Please help me with this thing :-k Waiting patiently for any replies.

Ben

---

