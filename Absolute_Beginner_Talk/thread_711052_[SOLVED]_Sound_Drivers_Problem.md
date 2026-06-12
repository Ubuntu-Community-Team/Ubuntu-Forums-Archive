---
title: "[SOLVED] Sound Drivers Problem"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by 4l13n666 on 2008-02-29
I have recently installed the new driver for my HP Pavillion dv6000 using the following command in the Terminal

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16rc1.tar.bz2)
tar xvpjf alsa-driver-1.0.16rc1.tar.bz2
cd alsa-driver-1.0.16rc1
./configure --with-cards=hda-intel
make
sudo make install

The driver got downloaded without any problems but i got some error messages when i tried installing it like the following:

In file included from /home/erik/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:29,
                 from /home/erik/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
include/linux/utsname.h:76:52: error: macro "init_utsname" passed 1 arguments, but takes just 0
In file included from /home/erik/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:29,
                 from /home/erik/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
include/linux/utsname.h:77: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
In file included from /home/erik/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
/home/erik/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c: In function ‘snd_sndstat_proc_read’:
/home/erik/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: ‘system_utsname’ undeclared (first use in this function)
/home/erik/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: (Each undeclared identifier is reported only once
/home/erik/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: for each function it appears in.)
make[3]: *** [/home/erik/alsa-driver-1.0.16rc1/acore/info_oss.o] Error 1
make[2]: *** [/home/erik/alsa-driver-1.0.16rc1/acore] Error 2
make[1]: *** [_module_/home/erik/alsa-driver-1.0.16rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [compile] Error 2
erik@erik-laptop:~/alsa-driver-1.0.16rc1$ sudo make install
if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/erik/alsa-driver-1.0.16rc1/include/sound /usr/include/sound; \
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
make[1]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/acore'
mkdir -p /lib/modules/2.6.22-14-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.22-14-generic/kernel/sound/acore
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rtctimer.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/acore'
make: *** [install-modules] Error 1
erik@erik-laptop:~/alsa-driver-1.0.16rc1$

So i restarted my laptop and now when i try opening the sound settings at the "Speaker icon" at the top of the right hand corner of the screen i get the following error message:

"No volume control GStreamer plugins and/or devices found."

What am i supposed to do in order to get my sound working? I really need my sound to work because Ubuntu is the best OS i have ever used and i would like to continue using it!

---

### Post by renzokuken on 2008-02-29
did you have build-essential package installed first?

if not run

```
sudo apt-get install build-essential
```

and try again

---

### Post by 4l13n666 on 2008-02-29
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Is the output i got.

---

### Post by renzokuken on 2008-02-29
then its already installed so compilation should work

also, you realise that 1.0.16rc1 is not a stable release, but a release candidate (the first of 3 usually). maybe try 1.0.15  instead and see if that works.

also, did you run the commands one at a time waiting for each to finish before starting the next?

---

### Post by 4l13n666 on 2008-02-29
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rtctimer.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/acore'
make: *** [install-modules] Error 1

I forgot to paste this i think as well. Any thoughts? If i should install 1.0.15, can you paste a command for the terminal i should use? And if i need to install it, do i need to uninstall the previous one?

---

### Post by 4l13n666 on 2008-02-29
> **renzokuken said:**
> then its already installed so compilation should work

also, you realise that 1.0.16rc1 is not a stable release, but a release candidate (the first of 3 usually). maybe try 1.0.15  instead and see if that works.

also, did you run the commands one at a time waiting for each to finish before starting the next?

No i don't know. I just copied the entire command that i was given and pasted it in the terminal and it started working the command by itself.

---

### Post by renzokuken on 2008-02-29
ahhh, in that case, there is your problem.

run the commands one at a time in the following order, waiting for each one to finish before starting the next

1.```
cd alsa-driver-1.0.16rc1
```


2.```
./configure --with-cards=hda-intel
```


3.```
make
```


4.```
sudo make install
```

---

### Post by 4l13n666 on 2008-02-29
This is what i got, which is the same as before even though i installed it in the given order. Do i need to uninstall first and reinstall? If so, how.

erik@erik-laptop:~$ cd alsa-driver-1.0.16rc1
erik@erik-laptop:~/alsa-driver-1.0.16rc1$ 
erik@erik-laptop:~/alsa-driver-1.0.16rc1$ ./configure --with-cards=hda-intel
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
checking for current directory... /home/erik/alsa-driver-1.0.16rc1
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
checking for kernel linux/seq_file.h... yes
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
checking for driver version... 1.0.16rc1
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
checking for init_utsname... no
checking for PnP suspend/resume... yes
checking for new unlocked/compat_ioctl... yes
checking for x86-compatible PC... yes
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for which soundcards to compile driver for... hda-intel
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
erik@erik-laptop:~/alsa-driver-1.0.16rc1$ make
make dep
make[1]: Entering directory `/home/erik/alsa-driver-1.0.16rc1'
make[2]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/acore'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/acore/ioctl32'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/acore/ioctl32'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/acore/oss'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/acore/oss'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/acore/seq'
make[4]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/acore/seq/oss'
make[4]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/acore/seq/oss'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/acore/seq'
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/acore'
make[2]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/i2c'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/i2c/l3'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/i2c/l3'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/i2c/other'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/i2c/other'
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/i2c'
make[2]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/drivers'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/drivers/mpu401'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/drivers/mpu401'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/drivers/opl3'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/drivers/opl3'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/drivers/opl4'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/drivers/opl4'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/drivers/pcsp'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/drivers/pcsp'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/drivers/vx'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/drivers/vx'
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/drivers'
make[2]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/isa'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/isa/ad1816a'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/isa/ad1816a'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/isa/ad1848'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/isa/ad1848'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/isa/cs423x'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/isa/cs423x'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/isa/es1688'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/isa/es1688'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/isa/gus'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/isa/gus'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/isa/msnd'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/isa/msnd'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/isa/opti9xx'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/isa/opti9xx'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/isa/sb'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/isa/sb'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/isa/wavefront'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/isa/wavefront'
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/isa'
make[2]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/synth'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/synth/emux'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/synth/emux'
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/synth'
make[2]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/ac97'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/ac97'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/ali5451'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/ali5451'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/asihpi'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/asihpi'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/au88x0'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/au88x0'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/ca0106'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/ca0106'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/cs46xx'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/cs46xx'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/cs5535audio'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/cs5535audio'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/echoaudio'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/echoaudio'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/emu10k1'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/emu10k1'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/hda'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/hda'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/ice1712'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/ice1712'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/korg1212'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/korg1212'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/mixart'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/mixart'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/nm256'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/nm256'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/oxygen'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/oxygen'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/pcxhr'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/pcxhr'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/pdplus'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/pdplus'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/riptide'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/riptide'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/rme9652'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/rme9652'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/trident'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/trident'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/vx222'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/vx222'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pci/ymfpci'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci/ymfpci'
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pci'
make[2]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/aoa'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/aoa/codecs'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/aoa/codecs'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/aoa/core'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/aoa/core'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/aoa/fabrics'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/aoa/fabrics'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/aoa/soundbus'
make[4]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/aoa/soundbus'
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/aoa'
make[2]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/soc'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/soc/at91'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/soc/at91'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/soc/codecs'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/soc/codecs'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/soc/fsl'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/soc/fsl'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/soc/pxa'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/soc/pxa'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/soc/s3c24xx'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/soc/s3c24xx'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/soc/sh'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/soc/sh'
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/soc'
make[2]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/usb'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/usb/caiaq'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/usb/caiaq'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/usb/usx2y'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/usb/usx2y'
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/usb'
make[2]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pcmcia'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/pcmcia/vx'
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pcmcia/vx'
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/pcmcia'
make[1]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/erik/alsa-driver-1.0.16rc1  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/hwdep.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/memory_wrapper.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/memalloc.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/sgbuf.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/pcm.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/pcm_native.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/pcm_lib.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/pcm_timer.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/pcm_misc.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/pcm_memory.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/rtctimer.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/timer.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/wrappers.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/misc_driver.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/sound.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/init.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/memory.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/info.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/control.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/misc.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/device.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/isadma.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/sound_oss.o
  CC [M]  /home/erik/alsa-driver-1.0.16rc1/acore/info_oss.o
In file included from /home/erik/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:29,
                 from /home/erik/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
include/linux/utsname.h:76:52: error: macro "init_utsname" passed 1 arguments, but takes just 0
In file included from /home/erik/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:29,
                 from /home/erik/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
include/linux/utsname.h:77: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
In file included from /home/erik/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
/home/erik/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c: In function ‘snd_sndstat_proc_read’:
/home/erik/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: ‘system_utsname’ undeclared (first use in this function)
/home/erik/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: (Each undeclared identifier is reported only once
/home/erik/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: for each function it appears in.)
make[3]: *** [/home/erik/alsa-driver-1.0.16rc1/acore/info_oss.o] Error 1
make[2]: *** [/home/erik/alsa-driver-1.0.16rc1/acore] Error 2
make[1]: *** [_module_/home/erik/alsa-driver-1.0.16rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [compile] Error 2
erik@erik-laptop:~/alsa-driver-1.0.16rc1$ sudo make install
[sudo] password for erik:
if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/erik/alsa-driver-1.0.16rc1/include/sound /usr/include/sound; \
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
make[1]: Entering directory `/home/erik/alsa-driver-1.0.16rc1/acore'
mkdir -p /lib/modules/2.6.22-14-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.22-14-generic/kernel/sound/acore
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rtctimer.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/erik/alsa-driver-1.0.16rc1/acore'
make: *** [install-modules] Error 1
erik@erik-laptop:~/alsa-driver-1.0.16rc1$ 
erik@erik-laptop:~/alsa-driver-1.0.16rc1$

---

### Post by renzokuken on 2008-02-29
at a guess i would say that 1.0.16rc1 was built with a different compiler version than you have installed.

try 1.0.15 as i mentioned before and see if you have more luck with that.

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2
tar xjf alsa-driver-1.0.15.tar.bz2
cd alsa-driver-1.0.15
./configure --with-cards=hda-intel
make
sudo make install

```

remembering to run one line at a time waiting for the previous one to finish before starting the next

---

### Post by superprash2003 on 2008-02-29
try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by 4l13n666 on 2008-02-29
> **renzokuken said:**
> at a guess i would say that 1.0.16rc1 was built with a different compiler version than you have installed.

try 1.0.15 as i mentioned before and see if you have more luck with that.

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2
tar xjf alsa-driver-1.0.15.tar.bz2
cd alsa-driver-1.0.15
./configure --with-cards=hda-intel
make
sudo make install

```

remembering to run one line at a time waiting for the previous one to finish before starting the next

Alright the output of the command you provided me is as follows:

patching file ali5451.c 
Hunk #1 succeeded at 2209 (offset -8 lines). 
Hunk #2 succeeded at 2379 (offset -8 lines). 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/ali5451' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/asihpi' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/asihpi' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/au88x0' 
copying file alsa-kernel/pci/au88x0/au88x0.c 
patching file au88x0.c 
Hunk #2 succeeded at 342 (offset 1 line). 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/au88x0' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/ca0106' 
copying file alsa-kernel/pci/ca0106/ca0106_main.c 
patching file ca0106_main.c 
Hunk #1 succeeded at 169 (offset 4 lines). 
Hunk #2 succeeded at 1361 (offset 44 lines). 
Hunk #3 succeeded at 1730 (offset 49 lines). 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/ca0106' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/cmi8788' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/cmi8788' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/cs46xx' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/cs46xx' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/cs5535audio' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/cs5535audio' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/echoaudio' 
copying file alsa-kernel/pci/echoaudio/echoaudio.c 
patching file echoaudio.c 
Hunk #1 succeeded at 1897 (offset -29 lines). 
Hunk #2 succeeded at 1960 (offset -29 lines). 
copying file alsa-kernel/pci/echoaudio/darla20.c 
patching file darla20.c 
Hunk #2 succeeded at 107 (offset 2 lines). 
copying file alsa-kernel/pci/echoaudio/darla24.c 
patching file darla24.c 
Hunk #2 succeeded at 114 (offset 2 lines). 
copying file alsa-kernel/pci/echoaudio/echo3g.c 
patching file echo3g.c 
Hunk #2 succeeded at 128 (offset 4 lines). 
copying file alsa-kernel/pci/echoaudio/gina20.c 
patching file gina20.c 
Hunk #2 succeeded at 111 (offset 2 lines). 
copying file alsa-kernel/pci/echoaudio/gina24.c 
patching file gina24.c 
Hunk #2 succeeded at 135 (offset 6 lines). 
copying file alsa-kernel/pci/echoaudio/indigo.c 
patching file indigo.c 
Hunk #2 succeeded at 113 (offset 3 lines). 
copying file alsa-kernel/pci/echoaudio/indigodj.c 
patching file indigodj.c 
Hunk #2 succeeded at 113 (offset 3 lines). 
copying file alsa-kernel/pci/echoaudio/indigoio.c 
patching file indigoio.c 
Hunk #2 succeeded at 114 (offset 3 lines). 
copying file alsa-kernel/pci/echoaudio/layla20.c 
patching file layla20.c 
Hunk #2 succeeded at 121 (offset 3 lines). 
copying file alsa-kernel/pci/echoaudio/layla24.c 
patching file layla24.c 
Hunk #2 succeeded at 133 (offset 6 lines). 
copying file alsa-kernel/pci/echoaudio/mia.c 
patching file mia.c 
Hunk #2 succeeded at 126 (offset 3 lines). 
copying file alsa-kernel/pci/echoaudio/mona.c 
patching file mona.c 
Hunk #2 succeeded at 144 (offset 9 lines). 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/echoaudio' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/emu10k1' 
copying file alsa-kernel/pci/emu10k1/emu10k1_main.c 
patching file emu10k1_main.c 
copying file alsa-kernel/pci/emu10k1/emu10k1x.c 
patching file emu10k1x.c 
Hunk #2 succeeded at 1628 (offset -7 lines). 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/emu10k1' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/hda' 
copying file alsa-kernel/pci/hda/hda_codec.c 
patching file hda_codec.c 
Hunk #2 succeeded at 278 (offset 21 lines). 
Hunk #3 succeeded at 316 (offset 21 lines). 
Hunk #4 succeeded at 331 (offset 21 lines). 
Hunk #5 succeeded at 347 (offset 21 lines). 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/hda' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/ice1712' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/ice1712' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/korg1212' 
copying file alsa-kernel/pci/korg1212/korg1212.c 
patching file korg1212.c 
Hunk #1 succeeded at 2342 (offset -1 lines). 
Hunk #2 succeeded at 2503 (offset -1 lines). 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/korg1212' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/mixart' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/mixart' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/nm256' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/nm256' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/pcxhr' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/pcxhr' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/pdplus' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/pdplus' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/riptide' 
copying file alsa-kernel/pci/riptide/riptide.c 
patching file riptide.c 
Hunk #1 succeeded at 1279 (offset 10 lines). 
Hunk #2 succeeded at 2236 (offset 10 lines). 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/riptide' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/rme9652' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/rme9652' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/trident' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/trident' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/vx222' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/vx222' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/ymfpci' 
copying file alsa-kernel/pci/ymfpci/ymfpci_main.c 
patching file ymfpci_main.c 
Hunk #2 succeeded at 2045 (offset -8 lines). 
Hunk #3 succeeded at 2067 (offset -8 lines). 
Hunk #4 succeeded at 2407 (offset -8 lines). 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/ymfpci' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/aoa' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/aoa/codecs' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/aoa/codecs' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/aoa/core' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/aoa/core' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/aoa/fabrics' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/aoa/fabrics' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/aoa/soundbus' 
make[4]: Entering directory `/home/erik/alsa-driver-1.0.15/aoa/soundbus/i2sbus' 
make[4]: Leaving directory `/home/erik/alsa-driver-1.0.15/aoa/soundbus/i2sbus' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/aoa/soundbus' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/aoa' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/soc' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/soc/at91' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/soc/at91' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/soc/codecs' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/soc/codecs' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/soc/pxa' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/soc/pxa' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/soc/s3c24xx' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/soc/s3c24xx' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/soc/sh' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/soc/sh' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/soc' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/usb' 
copying file alsa-kernel/usb/usbaudio.c 
patching file usbaudio.c 
Hunk #3 succeeded at 659 with fuzz 2 (offset -10 lines). 
Hunk #4 succeeded at 686 with fuzz 2 (offset -10 lines). 
Hunk #5 succeeded at 767 (offset -10 lines). 
Hunk #6 succeeded at 782 (offset -10 lines). 
Hunk #7 succeeded at 1160 (offset -10 lines). 
Hunk #8 succeeded at 2082 (offset 3 lines). 
Hunk #9 succeeded at 2101 (offset 3 lines). 
Hunk #10 succeeded at 2118 (offset 3 lines). 
Hunk #11 succeeded at 2675 (offset 13 lines). 
Hunk #12 succeeded at 2747 (offset 13 lines). 
Hunk #13 succeeded at 3035 (offset 17 lines). 
Hunk #14 succeeded at 3106 (offset 17 lines). 
Hunk #15 succeeded at 3227 (offset 69 lines). 
Hunk #16 succeeded at 3245 (offset 69 lines). 
Hunk #17 succeeded at 3259 (offset 69 lines). 
Hunk #18 succeeded at 3272 (offset 69 lines). 
Hunk #19 succeeded at 3476 (offset 77 lines). 
Hunk #20 succeeded at 3569 (offset 79 lines). 
Hunk #21 succeeded at 3706 (offset 78 lines). 
Hunk #22 succeeded at 3727 (offset 78 lines). 
Hunk #23 succeeded at 3748 (offset 78 lines). 
copying file alsa-kernel/usb/usbmidi.c 
patching file usbmidi.c 
Hunk #2 succeeded at 226 (offset 1 line). 
Hunk #3 succeeded at 250 (offset 1 line). 
Hunk #4 succeeded at 343 (offset 1 line). 
Hunk #5 succeeded at 1450 (offset 88 lines). 
Hunk #6 succeeded at 1798 (offset 92 lines). 
copying file alsa-kernel/usb/usbmixer.c 
patching file usbmixer.c 
Hunk #3 succeeded at 1725 (offset -1 lines). 
Hunk #4 succeeded at 1774 (offset -1 lines). 
Hunk #5 succeeded at 1795 (offset -1 lines). 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/usb/caiaq' 
copying file alsa-kernel/usb/caiaq/caiaq-audio.c 
patching file caiaq-audio.c 
copying file alsa-kernel/usb/caiaq/caiaq-device.c 
patching file caiaq-device.c 
Hunk #1 succeeded at 106 (offset 6 lines). 
Hunk #2 succeeded at 313 (offset 14 lines). 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/usb/caiaq' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/usb/usx2y' 
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c 
patching file usX2Yhwdep.c 
Hunk #3 succeeded at 63 with fuzz 2. 
copying file alsa-kernel/usb/usx2y/usbusx2y.c 
patching file usbusx2y.c 
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c 
patching file usbusx2yaudio.c 
Hunk #10 succeeded at 1057 (offset -1 lines). 
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c 
patching file usx2yhwdeppcm.c 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/usb/usx2y' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/usb' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pcmcia' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pcmcia/pdaudiocf' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pcmcia/pdaudiocf' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/pcmcia/vx' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/pcmcia/vx' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pcmcia' 
make[1]: Leaving directory `/home/erik/alsa-driver-1.0.15' 
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/erik/alsa-driver-1.0.15  CPP="gcc -E" CC="gcc" modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic' 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/hwdep.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/memory_wrapper.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/memalloc.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/sgbuf.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/pcm.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/pcm_native.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/pcm_lib.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/pcm_timer.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/pcm_misc.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/pcm_memory.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/rtctimer.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/timer.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/wrappers.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/misc_driver.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/sound.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/init.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/memory.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/info.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/control.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/misc.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/device.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/isadma.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/sound_oss.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/info_oss.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/snd.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/snd-hwdep.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/snd-timer.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/snd-rtctimer.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/snd-pcm.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/snd-page-alloc.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/oss/mixer_oss.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/oss/pcm_oss.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/oss/pcm_plugin.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/oss/io.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/oss/copy.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/oss/linear.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/oss/mulaw.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/oss/route.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/oss/rate.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/oss/snd-mixer-oss.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/oss/snd-pcm-oss.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/seq_device.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/seq_midi_event.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/seq.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/seq_lock.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/seq_clientmgr.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/seq_memory.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/seq_queue.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/seq_fifo.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/seq_prioq.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/seq_timer.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/seq_system.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/seq_ports.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/seq_info.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/seq/snd-seq.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/seq/snd-seq-device.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/seq/snd-seq-midi-event.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/oss/seq_oss.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/oss/seq_oss_init.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/oss/seq_oss_timer.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/oss/seq_oss_ioctl.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/oss/seq_oss_event.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/oss/seq_oss_rw.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/oss/seq_oss_synth.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/oss/seq_oss_midi.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/oss/seq_oss_readq.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/acore/seq/oss/seq_oss_writeq.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/seq/oss/snd-seq-oss.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/pci/hda/hda_intel.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/pci/hda/hda_codec.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/pci/hda/hda_proc.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/pci/hda/hda_hwdep.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/pci/hda/hda_generic.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/pci/hda/patch_realtek.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/pci/hda/patch_cmedia.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/pci/hda/patch_analog.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/pci/hda/patch_sigmatel.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/pci/hda/patch_si3054.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/pci/hda/patch_atihdmi.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/pci/hda/patch_conexant.o 
  CC [M]  /home/erik/alsa-driver-1.0.15/pci/hda/patch_via.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/pci/hda/snd-hda-intel.o 
  Building modules, stage 2. 
  MODPOST 13 modules 
  CC      /home/erik/alsa-driver-1.0.15/acore/oss/snd-mixer-oss.mod.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/oss/snd-mixer-oss.ko 
  CC      /home/erik/alsa-driver-1.0.15/acore/oss/snd-pcm-oss.mod.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/oss/snd-pcm-oss.ko 
  CC      /home/erik/alsa-driver-1.0.15/acore/seq/oss/snd-seq-oss.mod.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/seq/oss/snd-seq-oss.ko 
  CC      /home/erik/alsa-driver-1.0.15/acore/seq/snd-seq-device.mod.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/seq/snd-seq-device.ko 
  CC      /home/erik/alsa-driver-1.0.15/acore/seq/snd-seq-midi-event.mod.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/seq/snd-seq-midi-event.ko 
  CC      /home/erik/alsa-driver-1.0.15/acore/seq/snd-seq.mod.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/seq/snd-seq.ko 
  CC      /home/erik/alsa-driver-1.0.15/acore/snd-hwdep.mod.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/snd-hwdep.ko 
  CC      /home/erik/alsa-driver-1.0.15/acore/snd-page-alloc.mod.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/snd-page-alloc.ko 
  CC      /home/erik/alsa-driver-1.0.15/acore/snd-pcm.mod.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/snd-pcm.ko 
  CC      /home/erik/alsa-driver-1.0.15/acore/snd-rtctimer.mod.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/snd-rtctimer.ko 
  CC      /home/erik/alsa-driver-1.0.15/acore/snd-timer.mod.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/snd-timer.ko 
  CC      /home/erik/alsa-driver-1.0.15/acore/snd.mod.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/acore/snd.ko 
  CC      /home/erik/alsa-driver-1.0.15/pci/hda/snd-hda-intel.mod.o 
  LD [M]  /home/erik/alsa-driver-1.0.15/pci/hda/snd-hda-intel.ko 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic' 
utils/link-modules /home/erik/alsa-driver-1.0.15 

ALSA modules were successfully compiled. 

erik@erik-laptop:~/alsa-driver-1.0.15$ sudo make install 
[sudo] password for erik: 
if [ -L /usr/include/sound ]; then \ 
                rm -f /usr/include/sound; \ 
                ln -sf /home/erik/alsa-driver-1.0.15/include/sound /usr/include/sound; \ 
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
make[1]: Entering directory `/home/erik/alsa-driver-1.0.15/acore' 
mkdir -p /lib/modules/2.6.22-14-generic/kernel/sound/acore 
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.22-14-generic/kernel/sound/acore 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/acore/ioctl32' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/acore/ioctl32' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/acore/oss' 
mkdir -p /lib/modules/2.6.22-14-generic/kernel/sound/acore/oss 
cp snd-mixer-oss.ko snd-pcm-oss.ko /lib/modules/2.6.22-14-generic/kernel/sound/acore/oss 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/acore/oss' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/acore/seq' 
mkdir -p /lib/modules/2.6.22-14-generic/kernel/sound/acore/seq 
cp snd-seq-device.ko snd-seq-midi-event.ko snd-seq.ko /lib/modules/2.6.22-14-generic/kernel/sound/acore/seq 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/acore/seq/instr' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/acore/seq/instr' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/acore/seq/oss' 
mkdir -p /lib/modules/2.6.22-14-generic/kernel/sound/acore/seq/oss 
cp snd-seq-oss.ko /lib/modules/2.6.22-14-generic/kernel/sound/acore/seq/oss 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/acore/seq/oss' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/acore/seq' 
make[1]: Leaving directory `/home/erik/alsa-driver-1.0.15/acore' 
make[1]: Entering directory `/home/erik/alsa-driver-1.0.15/i2c' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/i2c/l3' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/i2c/l3' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/i2c/other' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/i2c/other' 
make[1]: Leaving directory `/home/erik/alsa-driver-1.0.15/i2c' 
make[1]: Entering directory `/home/erik/alsa-driver-1.0.15/drivers' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/drivers/mpu401' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/drivers/mpu401' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/drivers/opl3' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/drivers/opl3' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/drivers/opl4' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/drivers/opl4' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/drivers/pcsp' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/drivers/pcsp' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/drivers/vx' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/drivers/vx' 
make[1]: Leaving directory `/home/erik/alsa-driver-1.0.15/drivers' 
make[1]: Entering directory `/home/erik/alsa-driver-1.0.15/isa' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/isa/ad1816a' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/isa/ad1816a' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/isa/ad1848' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/isa/ad1848' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/isa/cs423x' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/isa/cs423x' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/isa/es1688' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/isa/es1688' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/isa/gus' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/isa/gus' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/isa/msnd' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/isa/msnd' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/isa/opti9xx' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/isa/opti9xx' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/isa/sb' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/isa/sb' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/isa/wavefront' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/isa/wavefront' 
make[1]: Leaving directory `/home/erik/alsa-driver-1.0.15/isa' 
make[1]: Entering directory `/home/erik/alsa-driver-1.0.15/synth' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/synth/emux' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/synth/emux' 
make[1]: Leaving directory `/home/erik/alsa-driver-1.0.15/synth' 
make[1]: Entering directory `/home/erik/alsa-driver-1.0.15/pci' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/ac97' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/ac97' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/ali5451' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/ali5451' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/asihpi' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/asihpi' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/au88x0' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/au88x0' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/ca0106' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/ca0106' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/cmi8788' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/cmi8788' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/cs46xx' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/cs46xx' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/cs5535audio' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/cs5535audio' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/echoaudio' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/echoaudio' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/emu10k1' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/emu10k1' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/hda' 
mkdir -p /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda 
cp snd-hda-intel.ko /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/hda' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/ice1712' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/ice1712' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/korg1212' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/korg1212' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/mixart' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/mixart' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/nm256' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/nm256' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/pcxhr' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/pcxhr' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/pdplus' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/pdplus' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/riptide' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/riptide' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/rme9652' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/rme9652' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/trident' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/trident' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/vx222' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/vx222' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pci/ymfpci' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci/ymfpci' 
make[1]: Leaving directory `/home/erik/alsa-driver-1.0.15/pci' 
make[1]: Entering directory `/home/erik/alsa-driver-1.0.15/aoa' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/aoa/codecs' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/aoa/codecs' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/aoa/core' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/aoa/core' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/aoa/fabrics' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/aoa/fabrics' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/aoa/soundbus' 
make[3]: Entering directory `/home/erik/alsa-driver-1.0.15/aoa/soundbus/i2sbus' 
make[3]: Leaving directory `/home/erik/alsa-driver-1.0.15/aoa/soundbus/i2sbus' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/aoa/soundbus' 
make[1]: Leaving directory `/home/erik/alsa-driver-1.0.15/aoa' 
make[1]: Entering directory `/home/erik/alsa-driver-1.0.15/soc' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/soc/at91' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/soc/at91' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/soc/codecs' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/soc/codecs' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/soc/pxa' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/soc/pxa' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/soc/s3c24xx' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/soc/s3c24xx' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/soc/sh' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/soc/sh' 
make[1]: Leaving directory `/home/erik/alsa-driver-1.0.15/soc' 
make[1]: Entering directory `/home/erik/alsa-driver-1.0.15/usb' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/usb/caiaq' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/usb/caiaq' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/usb/usx2y' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/usb/usx2y' 
make[1]: Leaving directory `/home/erik/alsa-driver-1.0.15/usb' 
make[1]: Entering directory `/home/erik/alsa-driver-1.0.15/pcmcia' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pcmcia/pdaudiocf' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pcmcia/pdaudiocf' 
make[2]: Entering directory `/home/erik/alsa-driver-1.0.15/pcmcia/vx' 
make[2]: Leaving directory `/home/erik/alsa-driver-1.0.15/pcmcia/vx' 
make[1]: Leaving directory `/home/erik/alsa-driver-1.0.15/pcmcia' 
/sbin/depmod -a 2.6.22-14-generic 
cat WARNING 

WARNING!!! The mixer channels for the ALSA driver are muted by default!!! 
************************************************************************** 
You would use some ALSA or OSS mixer to set the appropriate volume. 


This i think means that the install was successful. But i still do not have any SOUND DEVICE. So i cannot open "alsamixer" by running it as a terminal command. When i right click on the speaker in the right top hand corner ( which has a mute symbol on it ) i get the following message: "No volume control GStreamer plugins and/or devices found."

Any suggestions?

---

### Post by renzokuken on 2008-03-03
alsa did indeed install correctly this time. did you reboot?

try going to System -> Preferences -> Sound and making sure Alsa is selected in the boxes under the "Devices" tab.

failing that, i'm out of ideas, but someone else will know

incidentally, could you post the output of the two follwing commands

```
lspci
``` and ```
lsusb
```

---

