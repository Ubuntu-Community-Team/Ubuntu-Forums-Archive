---
title: "[SOLVED] Problems &amp;quot;making&amp;quot; alsa for headphone fix"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by marco_polo99 on 2007-11-25
After two weeks of spending all of my free time to achieve my first linux installation I'm up and running, but now moving to "smaller" problems--such as the headphones not working--I plug them in and the sound continues out of the speakers as always with none in headphones.  I followed the directions in [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
but when I try to make and or make install the driver I get errors that I don't understand.  I saw a similar post, but it was never resolved.  Can someone help.  Below is the output from make and make install


Your help would seriously boost my flagging ubuntu spirits!
Thanks

mark@mark-laptop:/usr/src/alsa/alsa-driver-1.0.9rc4a$ sudo make
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
mark@mark-laptop:/usr/src/alsa/alsa-driver-1.0.9rc4a$ sudo make installrm -f /lib/modules/0.0.0/misc/snd*.*o /lib/modules/0.0.0/misc/persist.o /lib/modules/0.0.0/misc/isapnp.o
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
mkdir -p /lib/modules/0.0.0/misc
cp snd-hpet.o snd-page-alloc.o snd-pcm.o snd-timer.o snd.o /lib/modules/0.0.0/misc
cp: cannot stat `snd-hpet.o': No such file or directory
cp: cannot stat `snd-page-alloc.o': No such file or directory
cp: cannot stat `snd-pcm.o': No such file or directory
cp: cannot stat `snd-timer.o': No such file or directory
cp: cannot stat `snd.o': No such file or directory
make[1]: *** [_modinst__] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
make: *** [install-modules] Error 1

---

### Post by FuturePilot on 2007-11-25
ALSA 1.0.9rc4 is very old. 1.0.15 is the latest version.
Have you tried manually muting the main speakers? I have a similar issue with my laptop and as soon as I mute the speakers the headphones work.

---

### Post by marco_polo99 on 2007-11-25
Thanks for the heads up on the version of alsa--I had gone to downloads page and went to the bottom where one would think that you would find the newest version, but the naming convention put the newest version in the middle--go figure--will download newest and retry.  

Otherwise my volume just has a master and PCM and muting either one doesn't change anything.

---

### Post by marco_polo99 on 2007-11-25
Downloaded newest version of driver, utilities and library. Driver and library worked okay w/ config and make, but utilities gives errors (see below) Thought maybe would work after reboot anyway, but no.  Also is there another location to control volume other than panel that opens with double click on speaker icon?

ps in case it matters, my laptop is a sony vaio vgn-fz240e
Thanks!

mark@mark-laptop:/usr/src/alsa/alsa-utils-1.0.15$ sudo make
Making all in include
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.15/include'
make  all-am
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.15/include'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.15/include'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.15/include'
Making all in alsactl
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.15/alsactl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.15/alsactl'
Making all in alsaconf
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.15/alsaconf'
Making all in po
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.15/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.15/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.15/alsaconf'
make: *** [all-recursive] Error 1
mark@mark-laptop:/usr/src/alsa/alsa-utils-1.0.15$ sudo make installMaking install in include
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.15/include'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.15/include'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.15/include'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.15/include'
Making install in alsactl
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.15/alsactl'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.15/alsactl'
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.15/alsactl'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.15/alsactl'
Making install in alsaconf
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.15/alsaconf'
Making install in po
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.15/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.15/alsaconf/po'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.15/alsaconf'
make: *** [install-recursive] Error 1
mark@mark-laptop:/usr/src/alsa/alsa-utils-1.0.15$

---

### Post by marco_polo99 on 2007-11-26
I solved the problems with "make" and the alsa directories.  Despite having a gettext library apparently I needed another, so I downloaded anything that looked relevant from synaptic (note under settings you must change repositories in order to see more software packages) Also see post [http://www.linuxquestions.org/questions/linux-software-2/alsa-utils-1.0.8-fails-during-make-294058/](http://www.linuxquestions.org/questions/linux-software-2/alsa-utils-1.0.8-fails-during-make-294058/)

Now everything compiles/ makes/installs okay and I added text into all of the suggested files from the following post [http://ubuntuforums.org/showthread.php?t=76307](http://ubuntuforums.org/showthread.php?t=76307)  but still no sound from the headphone jack.  There is also no new mixer as promised--still just the alsa mixer with Master and PCM.  After investing 12 hrs into this fix I'm still no closer--help please...

laptop is sony vaio vgn-fz240e

---

### Post by marco_polo99 on 2007-12-02
Solved the headphone issue by reinstalling alsa according to instructions provided by LordRaiden [http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+mixer](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+mixer)  then downloading alsa mixer gui  "sudo apt-get install alsamixergui" and adding line "options snd-hda-intel model=vaio position_fix=0" into /etc/modprobe.d/alsa-base

---

