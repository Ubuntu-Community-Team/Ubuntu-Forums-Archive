---
title: "I don't understand how to follow the directions of this wiki..."
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Scott O'Nanski on 2008-01-18
I'm a little confused about the following directions from "Setup Installation Directory" portion from the following Wiki;


[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28Intel%29%7C%28HDA%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28Intel%29%7C%28HDA%29)

I've trying to understand to the best of my capabilities of the information being provided, but I'm a little stumped. When I follow the wiki, I run into problems almost immediately as mentioned below; 

sudo mkdir -p /usr/src/alsa (No problem here)
cd /usr/src/alsa (No problem here either)
sudo cp ~/downloads/alsa* . (This is what I don't comprehend)

I've downloaded the the compressed files (tar balls?) to the following directory "/home/myuseraccount;)/downloads/, but after I type the above command in the terminal - the following message is  bounced back;

"cp: cannot stat `/home/myuseraccount;)/downloads/alsa* .': No such file or directory"

I'm not too sure if the author of the document is using a generalized abbreviation "alsa*" and assumes the reader inherently understands his intent, or if perhaps the error lies in my understanding of where to place the files in my home directory.

I'm very new to Linux, so I'm a little overwhelmed at the lack of simplistic directions in the various documentation I've search so far.

If anyone can help it would be appreciated.

Please restrain the need to point me to google - I'm looking for something more efficient and pramatic.

Thanks.

---

### Post by p_quarles on 2008-01-18
> **Scott O'Nanski said:**
> 
sudo cp ~/downloads/alsa* . (This is what I don't comprehend)
That command is slightly off, but it sound like you haven't unpacked the tarball yet. Go back to the download dir, and then type:
```
tar -zxvf name-of-file.tar.gz
```
Then, back to /usr/src/alsa, and:
```
sudo cp ~/home/downloads/alsa/* .
```
(notice the slash before the asterisk).

---

### Post by az on 2008-01-18
The wiki page forgets to tell you to uncompress the alsa driver tarball files you download:

Ex:
tar xvjf alsa-driver-1.0.15.tar.bz2

Use xvzf for .tar.gz files instead of the "j" for bz2 compressed archives.

---

### Post by Scott O'Nanski on 2008-01-18
When I type;

```
tar -xvzf alsa-driver-1.0.9rc4a.tar.bz2
```

I get;

```
gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

```

I have no idea what this is telling me except "no". :(

Oh, i have an idea!! 

I can extract the files without having to use the terminal, then back to /usr/src/alsa THEN;

```
sudo cp ~/home/downloads/alsa/* .
```

---

### Post by p_quarles on 2008-01-18
Take a close look at az's post above. For the bz2 format, you need a different option:```
tar -xvjf alsa-driver-1.0.9rc4a.tar.bz2
```

---

### Post by Scott O'Nanski on 2008-01-18
> **p_quarles said:**
> That command is slightly off, but it sound like you haven't unpacked the tarball yet. Go back to the download dir, and then type:
```
tar -zxvf name-of-file.tar.gz
```
Then, back to /usr/src/alsa, and:
```
sudo cp ~/home/downloads/alsa/* .
```
(notice the slash before the asterisk).

Something's not right here...

```
sudo cp ~/home/downloads/alsa/* .
```

Gives me;

```
cp: cannot stat `/home/??????/home/downloads/alsa/*': No such file or directory
```

---

### Post by p_quarles on 2008-01-18
Oops! My bad. Sorry.

Should be either: ```
sudo cp /home/username/downloads/alsa/* .
``` or: ```
sudo cp ~/downloads/alsa/* .
```
Basically "~" and "/home/username" mean the same thing

---

### Post by Scott O'Nanski on 2008-01-18
Oh, man..,

This is nuts!

After I;

```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa/* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

```

I then attempt to compile and install alsa-driver/alsa-lib/alsa-util with the following;

```
cd alsa-driver*
```

I move on to this;

```
sudo ./configure --with-cards=hda-intel
```

I get the follwing information;

```
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver-1.0.9rc4a
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.22-14-generic/build
checking for directory with kernel build... 
checking for kernel version... 0.0.0
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... "no"
checking for existing ALSA module... "yes"
checking for Red Hat kernel... "auto"
checking for Red Hat kernel... "no"
checking for SUSE kernel... "auto"
checking for SUSE kernel... "no"
checking to modify of kernel linux/kmod.h... "no"
checking for kernel linux/compiler.h... "yes"
checking for kernel linux/pm.h... "yes"
checking for kernel linux/spinlock.h... "yes"
checking for kernel linux/irq.h... "yes"
checking for kernel linux/threads.h... "yes"
checking for kernel linux/rwsem.h... "yes"
checking for kernel linux/gameport.h... "yes"
checking for kernel linux/devfs_fs_kernel.h... "no"
checking for kernel linux/highmem.h... "yes"
checking for kernel linux/workqueue.h... "yes"
Removing a dummy linux/workqueue.h.
checking for kernel linux/dma-mapping.h... "yes"
Removing a dummy linux/dma-mapping.h.
checking for kernel asm/hw_irq.h... "yes"
checking for kernel linux/device.h... "yes"
Removing a dummy linux/device.h.
checking for kernel linux/jiffies.h... "yes"
Removing a dummy linux/jiffies.h.
checking for kernel linux/compat.h... "yes"
Removing a dummy linux/compat.h.
checking for kernel linux/adb.h... "yes"
checking for kernel linux/cuda.h... "yes"
checking for kernel linux/pmu.h... "yes"
checking for kernel linux/moduleparam.h... "yes"
Removing a dummy linux/moduleparam.h.
checking for kernel linux/syscalls.h... "yes"
Removing a dummy linux/syscalls.h.
checking for kernel linux/firmware.h... "yes"
checking for exported symbol dump_stack... grep: /lib/modules/2.6.22-14-generic/build/kernel/ksyms.c: No such file or directory
"no"
checking for kernel module symbol versions... "yes"
checking for PCI support in kernel... "yes"
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for directory to store kernel modules... /lib/modules/0.0.0/misc
checking for verbose printk... on
checking for debug level... none
checking for processor type... i586
checking for i386 machine type... default
checking for SMP... "yes"
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... "yes"
checking for strlcpy... "no"
checking for snprintf... "no"
checking for vsnprintf... "no"
checking for scnprintf... "no"
checking for sscanf... "no"
checking for vmalloc_to_page... "no"
checking for old kmod... "yes"
checking for PDE... "no"
checking for pci_set_consistent_dma_mask... "no"
checking for pci_dev_present... "no"
checking for msleep... "no"
checking for tty->count is the atomic type... "no"
checking for io_remap_pfn_range... "no"
checking for new io_remap_page_range... "no"
checking for kcalloc... "no"
checking for saved_config_space in pci_dev... "no"
checking for old kill_fasync... "no"
checking for dma_addr_t... "no"
checking for MUTEX macros... "no"
Removing local linux/pnp.h.
checking for driver version... 1.0.9rc4a
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... "no"
checking for HPET support... "yes"
checking for Procfs support... "yes"
checking for USB support... "yes"
checking for PC-Speaker hook... "no"
checking for kernel PCMCIA
checking for PCMCIA support... "yes"
checking for PC9800 support in kernel... "no"
checking for parallel port support... "yes"
checking for which soundcards to compile driver for... hda-intel
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
Hacking autoconf.h...

```

Then when I try to move on to;

```
sudo make
```

I get the following;

```
if [ ! -d include/sound -a ! -L include/sound ]; then \
          ln -sf ../alsa-kernel/include include/sound ; \
        fi
cp -auvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
gcc -D__KERNEL__ -DMODULE=1 -I/usr/src/alsa/alsa-driver-1.0.9rc4a/include  -I/lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm-i386/mach-default -O2 -mpreferred-stack-boundary=2 -march=i586 -D__SMP__ -DCONFIG_SMP -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include -DMODVERSIONS -include /lib/modules/2.6.22-14-generic/build/include/linux/modversions.h  -DKBUILD_BASENAME=hpetimer   -c -o hpetimer.o hpetimer.c
cc1: error: /lib/modules/2.6.22-14-generic/build/include/linux/modversions.h: No such file or directory
In file included from hpetimer.c:22:
/usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:29:26: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.22-14-generic/build/include/asm/processor.h:22,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:9,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/linux/cpumask.h:88: error: ‘CONFIG_NR_CPUS’ undeclared here (not in a function)
In file included from /lib/modules/2.6.22-14-generic/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:9,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:83: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:83: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h: In function ‘cpuid_count’:
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 1 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 2 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 3 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 4 of ‘native_cpuid’ differ in signedness
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/slab.h:14,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/percpu.h:5,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/desc.h:11,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/elf.h:50,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:15,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h: At top level:
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h:43: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h:93: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h:305: error: requested alignment is not a constant
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:21,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/asm/module.h:64:2: error: #error unknown processor family
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/irq.h:13,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/irq.h:23,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/pid.h:4,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/sched.h:72,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/irq.h:13,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/irq.h:23,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/lib/modules/2.6.22-14-generic/build/include/linux/rcupdate.h:71: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/linux/rcupdate.h:74: error: requested alignment is not a constant
In file included from /lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/lib/modules/2.6.22-14-generic/build/include/linux/irq.h:176: error: requested alignment is not a constant
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:12: error: requested alignment is not a constant
make[1]: *** [hpetimer.o] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
make: *** [compile] Error 1

```

Is this a "compiling error" (not that I know exactly what that means) or something???

---

### Post by p_quarles on 2008-01-18
```
sudo apt-get install build-essential
```
should fix that.

---

### Post by Scott O'Nanski on 2008-01-18
> **p_quarles said:**
> ```
sudo apt-get install build-essential
```
should fix that.

Why? 

:D

build-essential is already the newest version.

---

### Post by aktiwers on 2008-01-18
> **Scott O'Nanski said:**
> Why? 

:D

build-essential is already the newest version.

Thats the Compiling tools :D
Edit: oh uh nevermind.. didnt see the last line in your message..

---

### Post by p_quarles on 2008-01-18
> **Scott O'Nanski said:**
> Why? 

:D

build-essential is already the newest version.
So it is. Hmm.

Try this:```
sudo apt-get build-dep alsa-base
```
And then try the compile instructions again.

---

### Post by Scott O'Nanski on 2008-01-18
> **p_quarles said:**
> So it is. Hmm.

Try this:```
sudo apt-get build-dep alsa-base
```
And then try the compile instructions again.

Okay, I think I understand? lol

Let me see if I can think along the same lines of Linux;

1) sudo - superuser do this

2) apt-get - package repository "thingy"

3) build-dep alsa-base - build dependencies alsa base?


Don't laugh... I'm trying very hard over here. :)

when I;

```
sudo apt-get build-dep alsa-base
```


I get;

```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by p_quarles on 2008-01-18
Yeah, you understand the command correctly.

Got to say I'm stumped here. I kinda see what's going on with the errors on that follow the "sudo make" command, but I've got no idea what to do about them. Hopefully someone who does will come along.

---

### Post by Scott O'Nanski on 2008-01-18
> **p_quarles said:**
> Yeah, you understand the command correctly.

Got to say I'm stumped here. I kinda see what's going on with the errors on that follow the "sudo make" command, but I've got no idea what to do about them. Hopefully someone who does will come along.

Dude, you're awesome. Thanks.

I learned something new today. wOOt.

I may have found something that works, I'll post it if everything goes according to plan.

---

### Post by Scott O'Nanski on 2008-01-18
Nope, didn't work.

---

