---
title: "I get an error running MAKE"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by B34ST1Y on 2007-12-10
I'm trying to compile / install some audio drivers (realtek) for my gutsy Ubuntu....and I can configure just fine...but when I run the MAKE command, I get this error at the bottom:

--------------------------------------


root@zer0cool:/home/b34st1y/Desktop/alsa-driver-1.0.9rc4a# make
make[1]: Entering directory `/home/b34st1y/Desktop/alsa-driver-1.0.9rc4a/acore'
gcc -D__KERNEL__ -DMODULE=1 -I/home/b34st1y/Desktop/alsa-driver-1.0.9rc4a/include  -I/lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm-i386/mach-default -O2 -mpreferred-stack-boundary=2 -march=i586 -D__SMP__ -DCONFIG_SMP -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include -DMODVERSIONS -include /lib/modules/2.6.22-14-generic/build/include/linux/modversions.h  -DKBUILD_BASENAME=hpetimer   -c -o hpetimer.o hpetimer.c
cc1: error: /lib/modules/2.6.22-14-generic/build/include/linux/modversions.h: No such file or directory
In file included from hpetimer.c:22:
/home/b34st1y/Desktop/alsa-driver-1.0.9rc4a/include/sound/driver.h:29:26: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.22-14-generic/build/include/asm/processor.h:22,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:9,
                 from /home/b34st1y/Desktop/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /home/b34st1y/Desktop/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/linux/cpumask.h:88: error: ‘CONFIG_NR_CPUS’ undeclared here (not in a function)
In file included from /lib/modules/2.6.22-14-generic/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:9,
                 from /home/b34st1y/Desktop/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /home/b34st1y/Desktop/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
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
                 from /home/b34st1y/Desktop/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /home/b34st1y/Desktop/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h: At top level:
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h:43: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h:93: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h:305: error: requested alignment is not a constant
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:21,
                 from /home/b34st1y/Desktop/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /home/b34st1y/Desktop/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
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
make[1]: Leaving directory `/home/b34st1y/Desktop/alsa-driver-1.0.9rc4a/acore'
make: *** [compile] Error 1
--------------------------------------------------------------------------------------------


anyone know what I need to do? Is it some noob easy thing i forgot?

---

### Post by jordanmthomas on 2007-12-10
Have you installed
```
sudo apt-get install build-essential
```?
You'll also want to install the kernel headers (if they're not already in build-essential)  This is where your build is failing...it cannot find the header files it is looking for.

---

### Post by B34ST1Y on 2007-12-10
how do I install the headers? I ran that cmd and i'm assuming the package is installed now...but I still get the exact same error. >.>

---

### Post by jordanmthomas on 2007-12-10
```
sudo apt-get install linux-headers-2.6.22-14-generic
```

---

### Post by B34ST1Y on 2007-12-10
```
root@zer0cool:/home/b34st1y/Desktop/alsa-driver-1.0.9rc4a# sudo apt-get install linux-headers-2.6.22-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.22-14-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libstdc++2.10-glibc2.2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

so is it already installed then? @.@

---

### Post by jordanmthomas on 2007-12-10
Yes, and it doesn't make sense that it can't find modversions.h since the headers package provides it.  

Just a question, why are you building as root?  Try building as a user and see if it's any different (shouldn't be, but you never know)

---

### Post by jordanmthomas on 2007-12-10
Actually, nevermind.  It is looking for your header files in /lib instead of /usr/src
Are you sure you ran the configure script correctly?

---

### Post by B34ST1Y on 2007-12-10
idk, I figured that way if there was any permission problems i'd be set. I logged out of root and re-ran it....same errors T_T

---

### Post by jordanmthomas on 2007-12-10
Try running configure again now that you have everything installed right.

---

### Post by B34ST1Y on 2007-12-10
I downloaded the source file from alsa-project.org (I think it's my ALC885 realtek card's sound drivers.....that's what i've been trying to do from the start, I just want sound! lol.  I don't know anything much beyond

cd to the de-tarred folder
./configure
make
make install


I think, lol

---

### Post by PmDematagoda on 2007-12-10
I realise that this does not solve your problem, but can't you use ALSA that comes automatically with Ubuntu?

---

### Post by jordanmthomas on 2007-12-10
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
This should help you.  
I'm not sure what's wrong with what you are doing, but follow this and everything should go alright.

---

### Post by B34ST1Y on 2007-12-10
the actual thing I'm after here is working sound. upon installing gutsy ubuntu....the sound mixer can be brought up and I can adjust the sliders....as well as apparently playback music, but obviously no sound comes out of the speakers..

---

### Post by B34ST1Y on 2007-12-10
so yea....if anyone knows an easier way to get it working...by all means tell me now! :-D  heh

---

### Post by B34ST1Y on 2007-12-10
I looked on that link, ALSA is installed but i STILL get no sound. The computer appears to think that the hardware checks out but I dont get anything at all.... :(

---

### Post by B34ST1Y on 2007-12-10
do I need to reboot after making any changes to the sound settings in the control panel?

---

### Post by jordanmthomas on 2007-12-10
Control panel?
I don't know what this is.

You will need to restart alsa after a recompilation.  In which case, a reboot will do this.

---

### Post by B34ST1Y on 2007-12-10
excuse my noob windows lingo lol.


main menu  > preferences > sound



and somehow i still get that same error. >.<   .....didnt' you say it looked like it was pointing to some other directory? I have the folder on my desktop....the one i'm compiling; is that a problem ?

---

### Post by jordanmthomas on 2007-12-10
> **B34ST1Y said:**
>  .....didnt' you say it looked like it was pointing to some other directory? I have the folder on my desktop....the one i'm compiling; is that a problem ?

No, it doesn't matter where it is.  If you followed all the instructions at the link I gave you then I do not know what could be wrong and someone who knows more than me about building software (it's a shame, I'm a Computer Science major too) might need to help out.

---

### Post by B34ST1Y on 2007-12-10
weird. so if I download a different sound pack thing from the alsa website, it's compiling and evidently installing right now. I'll keep you posted :-D YAY thx so much

---

### Post by B34ST1Y on 2007-12-11
-_- well it compiled and supposedly installed. But I reboot and now it tells me there is no sound device configured, and upon trying to configure it...my sound card doesn't show up.


is there a way I can somehow emulate the windows driver...?  kinda like ndiswrapper for wifi

---

### Post by B34ST1Y on 2007-12-11
ok now...I tried perhaps configuring, make, and make install     on a diff package.....and this is what I get:

```
b34st1y@zer0cool:~/Desktop/alsa-driver-1.0.12$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
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
checking for current directory... /home/b34st1y/Desktop/alsa-driver-1.0.12
checking cross compile... 
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build... 
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

```


whats the deal now???

---

### Post by B34ST1Y on 2007-12-11
*bump* someone please help me out here. :(

---

### Post by jordanmthomas on 2007-12-11
1.  Make sure you have kernel sources installed.
2.  do this:
go into /usr/src and list the directory names and find your kernel's sources
Then, make a symlink to the sources 
```
sudo ln -s /usr/src/linux-whatever-generic /usr/src/linux
```
run configure again

---

