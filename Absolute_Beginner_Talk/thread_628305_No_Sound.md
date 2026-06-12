---
title: "No Sound"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by POWERVICE on 2007-12-01
Hi,
     When I try to open the vol. control I have 'No volume control GStreamer plugins and/or devices found'.
   Can someone tell me how I install the  GStreamer. I am not sure whether this is a sensible question but I assume that it is some software that will activate my sound card.
Thanks

---

### Post by ajopaul on 2007-12-01
> **POWERVICE said:**
> Hi,
     When I try to open the vol. control I have 'No volume control GStreamer plugins and/or devices found'.
   Can someone tell me how I install the  GStreamer. I am not sure whether this is a sensible question but I assume that it is some software that will activate my sound card.
Thanks

This means that proper drivers are not installed for your sound card. what is the audio controller you find after you type ```
lspci
``` ?

---

### Post by quandary on 2007-12-01
just compile and install the latest alsa drivers.
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

---

### Post by POWERVICE on 2007-12-01
Thanks for your reply. My sound card is as below. 

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)



I have found the alsa-project which appears to list my sound card  (although it is not clear which one I actually have). The instructions are somewhat beyond me and I would say that anyone that was not a computer expert would struggle. For example on the quick installation section of the alsa web site it says 'If you are using Hg (Mercurial) then you need to type:'........................ Well I do not know what Hg is, let alone whether I am using it. This unfortunately is typical of the complexity of using UBUNTU.
  Is this the only way of getting the sound to work? I am really looking for the windows way where you download and install driver and restart. OR some instuctions - do this first, then this etc. etc. 
  UBUNTU seems to be unbelievably difficult to use if something does need to be set up.
Thanks in anticipation.

I have now been trying the how to set up sound on the main UBUNTU instructions. This was quite a lot of step by step instructions over a couple of hours but unfortunately they did not work for me. Please let me know if someone can help - it surely should not be impossible!!!!. This seems to be another area where windows is much better.

---

### Post by quandary on 2007-12-21
It's really not that hard. Just download the latest alsa-driver. Here's the url:
```

ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2

```

then unpack the archive.

Read the install instructions, they are in the file install.
open it from the gnome-terminal (Applications->Accessories->Terminal) with: 
```

gedit install

```

Here the install instructions from the install file:
```


		Advanced Linux Sound Architecture - Driver
		==========================================
			    Installation guide


The ALSA driver replaces the OSS/Free driver.  Since version 0.4.0,
ALSA has supported only 2.2 or later kernels. The 2.0 kernels are no
longer supported.

You must compile the kernel with sound support (CONFIG_SOUND on
2.2/2.4 kernels) either as module or built-in.  You do not need to
select any of the other sound modules apart from sound support.

Before installing this driver, it will be helpful to read carefully
the documentation for insmod, modprobe, kmod and for the isapnp
module if you have an ISA PnP soundcard.


Module option name change after 0.9.0rc3
========================================

Note that module option names were changed in 0.9.0rc4. The 'snd_' prefix
was removed. You may use script in utils directory (module-options) to
convert your older /etc/modules.conf to newer one.


Quick install
=============

1) You must have full configured source for the Linux kernel which you
   want to use for the ALSA drivers. Note that ALSA drivers are part
   of the kernel, so there is necessary to resolve all symbol dependencies
   between the used kernel and ALSA driver code. Partly installed kernels
   (for example from distributor makers) can be unuseable for this action.

2) You must turn on sound support (soundcore module).

3) Run './configure' script.

 * General Options
   If you do not want ISA PnP support, use --with-isapnp=no switch.
   If you do not want sequencer support, use --with-sequencer=no switch.
   If you do not want OSS/Free emulation, use --with-oss=no switch.
   If you have udev or devfs and want to use more than eight cards, use
   --enable-dynamic-minors switch.
   If you want to turn on debug mode, use --with-debug=full switch.
   If you want to debug soundcard detection, try --with-debug=detect switch.

 * Kernel Source Tree
   On 2.4/2.6 kernels, the location of the kernel source tree is
   parsed automatilly from the running kernel.
   If it's not in the standard place, specify the path via
   --with-kernel=<kernel_directory>. 
   On 2.6 kernels, the build directory has to be given via
   --with-build=<kernel_build_dir> option additionally, too.

 * Drivers to Compile
   The card drivers to be compiled can be selected via --with-cards option.
   Pass the card driver name without "snd-" prefix.  To specify
   multiple drivers, list names with comma (,).
   Passing "all" will compile all possible drivers (and this is the
   default choice).
   Some drivers have compile options.  They can be passed via
   --with-card-options option.  Multiple options can be passed with comma,
   too.  The default is "all".
   For available cards and options, see ./configure --help.

 * Example
      ./configure --with-debug=full
      ./configure --with-cards=sb16,emu10k1 --with-card-options=sb16-csp

4) Run 'make'.

5) Run 'make install' as root.
   If you have already a system with ALSA init script, you should install
   just only modules via 'make install-modules' so that the existing init
   script won't be replaced.

6) Run the './snddevices' script to create new sound devices in /dev directory.
   Skip this step, if you have already /dev/snd/* files, or if you're
   using a DEVFS or udev.

7) Edit your kernel module config (either /etc/modprobe.conf or
   /etc/modules.conf, depending on the kernel version). If you are not
   sure, what to do, you may try the alsaconf script available in
   the alsa-utils package.

8) Run 'modprobe snd-xxxx' where xxxx is the name of your card.
   Note: All ALSA ISA drivers support ISA PnP natively, so you don't need
         isapnptools any more.  Don't use both together.  It will
         conflict.  For disabling the ALSA ISA PnP support, specify
         --with-isapnp=no configure switch.

You can also look at the utils/alsasound file. This script is designed for
the RedHat distribution, but it can be used with other distributions which
use System V style rc init scripts.

Note: All mixer channels are muted by default. You must use a native
      or OSS mixer program to unmute appropriate channels (for example a
      mixer from the alsa-utils package).

Note: This document notices the /etc/modules.conf file. Many current
      distributions uses the old /etc/conf.modules file. Both names are
      valid.


Kernel Module Configurations
============================

See alsa-kernel/Documentation/ALSA-Configuration.txt
(or Documentation/sounds/alsa/ALSA-Configuration.txt in linux-2.6
 kernel tree).


Driver cannot be activated?
===========================

1) You can check your soundcard setup again and read this install file
   (module parameters) carefully.
2) If you have got ISA PnP soundcard:
   native ISA PnP support: is your setup in /proc/isapnp correct?
3) If you have *non*-ISA PnP card:
   set isapnp=0 module option?  Otherwise the driver probes only the
   ISA PnP cards.
3) The driver is not still working: remake driver with:
     ./configure --with-debug=detect; make clean; make
   Reinsert new driver modules to kernel and look to /var/log/messages if
   there are some messages. If these messages do not help you, please
   create a new ticket in our bug reporting system.


Compilation from HG sources
===========================

You need GNU packages autoconf and automake installed in your system
to compile HG (Mercurial) sources of alsa-driver package.

For compilation you can use these commands:

	make ALSAKERNELDIR=../alsa-kernel all-deps
		(if the alsa-kernel-dir is really there)
	aclocal
	autoconf
	./configure
	make dep
	make

The included hgcompile script does this job for you.

Note: Some automake packages have missing aclocal program. Use newer version
      in the case.


Cross-compiling
===============

Use '--with-cross=prefix' parameter for the configure script.

Example:
  './configure --with-cross=arm-linux- --with-kernel=/home/ipaq/kernel/linux'.

For 2.6 kernels, pass the same kernel path to --with-build option, too. 


Autoloading on 2.2/2.4 Kernels
==============================

On 2.2 or 2.4 kernels, you have to set the additional aliases for
auto-loading via kmod in /etc/modules.conf:

----- /etc/modules.conf
# ALSA portion
alias char-major-116 snd
# OSS/Free portion
alias char-major-14 soundcore
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
----- /etc/modules.conf

The aliases sound-service-x-y define the add-on modules for ALSA
OSS emulation.  For the second or later card, define more aliases
for mixer and pcm in addition, such as:

----- /etc/modules.conf
# OSS/Free portion - card #2
alias sound-service-1-0 snd-mixer-oss
alias sound-service-1-3 snd-pcm-oss
alias sound-service-1-12 snd-pcm-oss
----- /etc/modules.conf

You don't need to define service 1 and 8 for the second or later
cards.

If you want to autoclean your modules, you should put below line to your
/etc/crontab:

*/10 * * * *   root  /sbin/modprobe -rs snd-card-0 snd-card-1; /sbin/rmmod -as

You may also want to extend the soundcard list to follow your requirements.


DEVFS support
=============

The ALSA driver fully supports the devfs extension.
You should add lines below to your devfsd.conf file:

LOOKUP snd MODLOAD ACTION snd
REGISTER ^sound/.* PERMISSIONS root.audio 660
REGISTER ^snd/.* PERMISSIONS root.audio 660

Warning: These lines assume that you have the audio group in your system.
         Otherwise replace audio word with another group name (root for
         example).

When DEVFS is enabled, snd module has the following option:

    device_mode
		- permission mask for dynamic sound device filesystem
		- This is available only when DEVFS is enabled
		- Default: 0666
		- E.g.: device_mode=0660


Information about Additional Modules
====================================

  Module snd-msnd-pinnacle
  ------------------------

    Module for Turtle Beach MultiSound Pinnacle/Fiji soundcards.

    io		- Port # for pinnacle/fiji card
    irq		- IRQ # for pinnalce/fiji card
    mem		- Memory address (0xb0000, 0xc8000, 0xd0000, 0xd8000,
		  0xe0000 or 0xe8000)
    write_ndelay - enable write ndelay
    calibrate_signal - calibrate signal (?)

    Module supports only one card.

  Module snd-pdplus
  -----------------

    Module for Sek'D/Marian Prodif Plus soundcards.

    silent_exit	- Do not reset when driver is unloaded.
    init_adat	- Initialise the card in ADAT mode (instead of in digital stereo).

    This module supports multiple cards.

  Module snd-serialmidi
  ---------------------

    Module for generic serial MIDI adapters.

    sdev	- Device file string for serial device
		  (default = "/dev/ttyS0")
    speed	- Speed in bauds. (9600,19200,38400,57600,115200)
		  (default = 38400)
    adaptor	- Type of adaptor.
                  0 = Soundcanvas, 1 = MS-124T, 2 = MS-124W S/A,
		  3 = MS-124W M/B
    devices	- Number of devices assigned to the card.  Default is 1.
  		  When this is more than 1, multiple serial devices (up
		  to 8) are assigned to a single card.  The number of
		  the tail of the device file name is increased for
		  each device.
    handshake	- Enable/disable handshaking (default = 1)	

    This module supports multiple devices.

  Module snd-asihpi
  -----------------

    Module for AudioScience ASI soundcards

    This module supports multiple cards.
    The driver requires the firmware loader support on kernel.

  Module snd-pcsp
  ---------------

    Module for PC-Speaker driver.

    For X86 only.  The kernel patch is required in advance, found in
    utils/patches/pcsp-kernel-2.6.10-03.diff


Trouble Shooting
================

Unresolved symbol with RedHat 9
-------------------------------

Run depmod -ae and check which symbol is missing.
If the unresolved symbol is "schedule_work", this is because RedHat
shipped the kernel with incomplete implementation of workqueue.
For solving this problem, run the following on the top of alsa-driver
directory:

	% touch include/linux/workqueue.h

and run "make clean", "make" again.

```

Just extract the bz2 archive, and copy the entire folder to:
```

/usr/src

```

then go to the gnome-terminal again, and type:
```

cd /usr/src/alsa-driver-1.0.15

```

Now type:
```

sudo apt-get install gcc g++ autoconf automake 

```
Enter your password. Press enter.

Now type:
```

sudo ./configure

```

 press enter

Then type:
```

sudo  make

```

 press enter

now type
```
 
sudo make install

```
 press enter

skip step 6,7 and 8

restart linux
finished.

---

### Post by tjk on 2007-12-22
Thanks quandary for taking the time to post a reply.  I found many "fixes" that were very complex or that didn't work -- but your simple directions for an ALSA reinstallation worked for me.  It makes me VERY happy to have my sound back!   :):):):):)

---

### Post by High Camp on 2007-12-24
Hey

Thanks for the informative post. I never got the same errors as the OP but since I upgraded to Gutsy the ATI sound hasn't worked. I followed the instructions and got some errors so to be safe I rebooted and tried again. I still get the same errors but in the login screen I have sound, very odd. Now when I go to check my sound devices it shows "default" but not the "ATI" that was there before. On top of that when I go into the mixer settings there's no bars, no volume, no mic, nothing.

Here is the output from attempting to compile ALSA:
```
XXXX@XXXX:~$ cd /usr/src/alsa-driver-1.0.15
XXXX@XXXX:/usr/src/alsa-driver-1.0.15$ sudo ./configure
[sudo] password for XXXX:
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa-driver-1.0.15
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.22-14-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.22-14-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/latency.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.22-14-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... no
checking for video_get_drvdata... yes
checking for V4L1 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver version... 1.0.15
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... yes
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... yes
checking for nested class_device... yes
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for PnP suspend/resume... yes
checking for new unlocked/compat_ioctl... yes
checking for x86-compatible PC... yes
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for which soundcards to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
XXXX@XXXX:/usr/src/alsa-driver-1.0.15$ sudo  make
make dep
make[1]: Entering directory `/usr/src/alsa-driver-1.0.15'
make[2]: Entering directory `/usr/src/alsa-driver-1.0.15/acore'
copying file alsa-kernel/core/pcm.c
/usr/src/alsa-driver-1.0.15/utils/patch-alsa: 24: patch: not found
make[2]: *** [pcm.c] Error 1
make[2]: Leaving directory `/usr/src/alsa-driver-1.0.15/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/usr/src/alsa-driver-1.0.15'
make: *** [include/sndversions.h] Error 2
XXXX@XXXX:/usr/src/alsa-driver-1.0.15$ sudo make install
if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /usr/src/alsa-driver-1.0.15/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/usr/src/alsa-driver-1.0.15/acore'
mkdir -p /lib/modules/2.6.22-14-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.22-14-generic/kernel/sound/acore
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-rtctimer.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/usr/src/alsa-driver-1.0.15/acore'
make: *** [install-modules] Error 1
XXXX@XXXX:/usr/src/alsa-driver-1.0.15$ 
```

Help will be much appreciated,

---

### Post by quandary on 2007-12-25
run:
apt-get update

run:
sudo update-manager

run:
sudo update-manager-c

run:
apt-get install kernel-package libncurses5-dev fakeroot wget bzip2 g++ gcc

run:
apt-get upgrade gcc g++

run:
sudo apt-get install libasound2 libasound2-dev

and run:
sudo apt-get install linux-libc-dev

then retry installing the alsa driver

you can also try:
System->Preferences->Sound
And play around with the different options for the sound devices.

If the error persists, you could try to compile the Linux kernel to resolve the non-defined kernel compiler.

See my post on
[http://ubuntuforums.org/showthread.php?t=638146](http://ubuntuforums.org/showthread.php?t=638146)
for how to compile & install the latest Linux kernel.

---

### Post by quandary on 2007-12-25
> **tjk said:**
> 
Thanks quandary for taking the time to post a reply.  I found many "fixes" that were very complex or that didn't work -- but your simple directions for an ALSA reinstallation worked for me.  It makes me VERY happy to have my sound back!   :):):):):)


:lolflag: You're welcome

---

### Post by High Camp on 2008-01-12
Worked perfectly for me. I was sleeping in the dog house until I got sound working on my girlfriends puter.

Thanks,

---

### Post by quandary on 2008-01-13
> **High Camp said:**
> Worked perfectly for me. I was sleeping in the dog house until I got sound working on my girlfriends puter.

Thanks,

Yea, the dog's house isn't that comforting, isn't it ;-)
You're welcome.
Nice to see that i didn't waste my time by posting something that nobody really reads/needs ;-)

---

### Post by High Camp on 2008-01-14
I'm sleeping much better now and the dog's much happier.

I just discovered that the external volume control works, which it didn't before.

Thanks,

---

