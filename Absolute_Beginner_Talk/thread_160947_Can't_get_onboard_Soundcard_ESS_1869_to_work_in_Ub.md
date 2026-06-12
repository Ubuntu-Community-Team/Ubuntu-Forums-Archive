---
title: "Can't get onboard Soundcard ESS 1869 to work in Ubuntu."
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by cutthroat on 2006-04-16
I only just installed Ubuntu, and I am new to linux in general. So even though what I'm about to write/paste might sound advanced, i barely know what i'm doing :)

First off, lspci gives me:

> 
[Sooma] 0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (r ev 03)
[Sooma] 0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev  03)
[Sooma] 0000:00:0d.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 08)
[Sooma] 0000:00:0f.0 Ethernet controller: D-Link System Inc DWL-510 2.4GHz Wireless PCI Adapter (rev 20)
[Sooma] 0000:00:14.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
[Sooma] 0000:00:14.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
[Sooma] 0000:00:14.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
[Sooma] 0000:00:14.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
[Sooma] 0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/ 2X (rev 5c)


This seems to be my soundcard:
> 
[Sooma] 0000:00:14.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
[Sooma] 0000:00:14.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)


Using google, it seems that I'm supposed to use either OSS or ALSA.
Well... trying to get ALSA running gets me this:

> 
soma@Ubuntu:~/alsa-driver-0.5.12a$ sudo ./configure
loading cache ./config.cache
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for ranlib... (cached) ranlib
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking how to run the C preprocessor... (cached) gcc -E
checking for ANSI C header files... (cached) yes
checking for linux/fs.h... (cached) yes
checking for working const... (cached) yes
checking for inline... (cached) inline
checking whether time.h and sys/time.h may both be included... (cached) yes
checking whether gcc needs -traditional... (cached) no
checking for directory with kernel source... /usr/src/linux
checking for kernel version... 2.6.12-9-386
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for SGI/MIPS (HAL2) architecture... no
checking for directory to store kernel modules... /lib/modules/2.6.12-9-386/misc
checking for debug level... none
checking for processor type... i386
checking for SMP... no
checking for ISA PnP driver in kernel... yes
checking for ISA PnP support... yes
checking for driver version... 0.5.12a
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for which soundcards to compile driver for... all
creating ./config.status
creating Makefile.conf
creating snddevices
creating utils/alsa-driver.spec
creating cards.config
creating include/config.h
include/config.h is unchanged
creating include/config1.h
include/config1.h is unchanged
creating include/version.h
include/version.h is unchanged

soma@Ubuntu:~/alsa-driver-0.5.12a$ make

make[1]: Entering directory `/home/soma/alsa-driver-0.5.12a/kernel'
gcc   -DALSA_BUILD -D__KERNEL__ -O2 -mpreferred-stack-boundary=2 -march=i386 -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -pipe -I/usr/src/linux/include -I.. -DEXPORT_SYMTAB -c sound.c
In file included from sound.c:23:
../include/driver.h:66:31: error: linux/modversions.h: No such file or directory
In file included from ../include/driver.h:67,
                 from sound.c:23:
../include/sndversions.h:3:29: error: linux/modsetver.h: No such file or directory
In file included from /usr/src/linux/include/asm/processor.h:18,
                 from /usr/src/linux/include/asm/thread_info.h:17,
                 from /usr/src/linux/include/linux/thread_info.h:21,
                 from /usr/src/linux/include/linux/spinlock.h:12,
                 from /usr/src/linux/include/linux/capability.h:45,
                 from /usr/src/linux/include/linux/sched.h:7,
                 from /usr/src/linux/include/linux/module.h:10,
                 from ../include/driver.h:78,
                 from sound.c:23:
/usr/src/linux/include/asm/system.h: In function ‘__set_64bit_var’:
/usr/src/linux/include/asm/system.h:193: warning: dereferencing type-punned pointer will break strict-aliasing rules
/usr/src/linux/include/asm/system.h:193: warning: dereferencing type-punned pointer will break strict-aliasing rules
In file included from ../include/driver.h:90,
                 from sound.c:23:
/usr/src/linux/include/asm/irq.h:16:25: error: irq_vectors.h: No such file or directory
In file included from /usr/src/linux/include/asm/hardirq.h:6,
                 from /usr/src/linux/include/linux/hardirq.h:6,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from ../include/driver.h:100,
                 from sound.c:23:
/usr/src/linux/include/linux/irq.h: At top level:
/usr/src/linux/include/linux/irq.h:72: error: ‘NR_IRQS’ undeclared here (not in a function)
In file included from /usr/src/linux/include/linux/irq.h:74,
                 from /usr/src/linux/include/asm/hardirq.h:6,
                 from /usr/src/linux/include/linux/hardirq.h:6,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from ../include/driver.h:100,
                 from sound.c:23:
/usr/src/linux/include/asm/hw_irq.h:28: error: ‘NR_IRQ_VECTORS’ undeclared here (not in a function)
sound.c:73: error: syntax error before ‘devfs_handle’
sound.c:73: warning: type defaults to ‘int’ in declaration of ‘devfs_handle’
sound.c:73: warning: initialization makes integer from pointer without a cast
sound.c:73: warning: data definition has no type or storage class
sound.c: In function ‘alsa_sound_init’:
sound.c:507: warning: too many arguments for format
sound.c:508: warning: implicit declaration of function ‘devfs_register_chrdev’
sound.c:533: warning: implicit declaration of function ‘devfs_register’
sound.c:533: error: ‘DEVFS_FL_DEFAULT’ undeclared (first use in this function)
sound.c:533: error: (Each undeclared identifier is reported only once
sound.c:533: error: for each function it appears in.)
sound.c: In function ‘alsa_sound_exit’:
sound.c:563: error: ‘devfs_handle_t’ undeclared (first use in this function)
sound.c:563: error: syntax error before ‘master’
sound.c:569: error: ‘master’ undeclared (first use in this function)
sound.c:569: warning: implicit declaration of function ‘devfs_find_handle’
sound.c:569: error: ‘DEVFS_SPECIAL_CHR’ undeclared (first use in this function)
sound.c:570: warning: implicit declaration of function ‘devfs_unregister’
sound.c:590: warning: implicit declaration of function ‘devfs_unregister_chrdev’
make[1]: *** [sound.o] Error 1
make[1]: Leaving directory `/home/soma/alsa-driver-0.5.12a/kernel'
make: *** [compile] Error 1


Trying to get OSS running gets me:
> 
soma@Ubuntu:/tmp$ sudo ./oss-install
OSS/Linux kernel module not available. Cannot continue.
It is likely that some important Linux packages are not
installed in your system which makes installing OSS impossible.

The Linux (RPM) packages required before OSS can be installed are
kernel-source, gcc, binutils and make. You can find them from the install CD/DVD
or the web/ftp site which you used when installing the Linux distribution.

Please take a look at /usr/lib/oss/logs/soundconf.log for more info.


**********************************
Post install configuration failed.
**********************************

Code=256
All OSS files have been installed. However there are some problems
with loading the driver module(s).

Please take a look at /usr/lib/oss/logs/soundconf.log for more info.


even though it actually seems i have all of "kernel-source, gcc, binutils and make" installed. I see all of the above as installed in my "Synaptic Package Manager", and also:
> 
soma@Ubuntu:/tmp$ make
make: *** No targets specified and no makefile found.  Stop.
soma@Ubuntu:/tmp$ gcc
gcc: no input files


I really have *NO* idea what else to do. Please help =(
Thanks in advance,
ct

---

### Post by nethbar on 2006-04-16
you *do* seem like an experienced user.  lspci is a good start but unfortunately

[QUOTE=cutthroat]
This seems to be my soundcard:
Quote:
[Sooma] 0000:00:14.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
[Sooma] 0000:00:14.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
[/QUOTE]

neither of these is a sound card.  For future debugging, both are part of the motherboard (the first deals with ISA expansion cards and the second hard drives) and I can't imagine either not working and still having a any semblence of a usable computer.  

If the sound card is onboard, make sure that is enabled in the BIOS.  Have you had this card working before in a different OS?

Try out 
sudo alsoconf
first.  It can take a lot of the legwork out (unless you like a challenge).  It might take awhile for it to find it (tell it to look everywhere) as that should be an ISA card?  If it doesn't work - 

You might try this: (from linuxquestions.org HCL listing)
[http://www.linuxquestions.org/hcl/showproduct.php?product=470&cat=72](http://www.linuxquestions.org/hcl/showproduct.php?product=470&cat=72)

try
sudo -i
modprobe snd-es18xx
modprobe snd-pcm-oss
modprobe snd-mixer-oss
modprobe snd-seq-oss

(Can anyone tell me how to make these modules load automatically in [X]Ubuntu?  I only sound like an experienced user myself ;) )

Before you try your sound out, check your sound levels to make sure nothing is muted.

Luck.

---

### Post by theDahv on 2006-12-21
[http://www.oliyiptong.com/blog/2006/07/15/old-hardware-help-in-ubuntu/](http://www.oliyiptong.com/blog/2006/07/15/old-hardware-help-in-ubuntu/)

---

