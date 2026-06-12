---
title: "Creative Extigy Installation - How?"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by nilord on 2007-09-12
How could I install my Creative Extigy in Ubuntu?
 
With the front Panel (Volume Knob, CMSS, etc.) working?
 
It is taking me months to find the perfect solution for this.
 
I tried using the exaudio driver installation found here: [http://exaudio.sourceforge.net/](http://exaudio.sourceforge.net/)
 
but I can't seem to make it work.
 
Pls. help! thanks!

---

### Post by splintercellguy on 2007-09-12
Please explain what difficulty you are experiencing in trying to install exaudio?

---

### Post by nilord on 2007-09-12
I really can't understand how to use it.
 
Im a newbie in Linux, that's the hard part in this scenario.

---

### Post by splintercellguy on 2007-09-12
Have you read the instructions here: [http://exaudio.sourceforge.net/k26.html](http://exaudio.sourceforge.net/k26.html) Is there any part of it that you do not understand? By the way, you'll probably need build-essential and your Linux headers:

sudo apt-get install build-essential linux-headers-`uname -r`

---

### Post by nilord on 2007-09-12
I really can't understand everything. Except the Untar of course.

starting from Instruction #2, I really don't know how it is done.

But I tried to really understand the instructions and really tried to follow it.

I logged in as root, then untar-ed the source to my root

in the terminal, typed what you said:

sudo apt-get install build-essential linux-headers-`uname -r`

after updating, i typed:

make

it displayed this:

make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/root modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /root/audiofunc.o
/root/audiofunc.c: In function &#8216;start_stream&#8217;:
/root/audiofunc.c:599: warning: assignment from incompatible pointer type
/root/audiofunc.c:628: warning: assignment from incompatible pointer type
/root/audiofunc.c:645: warning: assignment from incompatible pointer type
/root/audiofunc.c:661: warning: assignment from incompatible pointer type
/root/audiofunc.c: In function &#8216;exaudio_mmap&#8217;:
/root/audiofunc.c:1187: error: dereferencing pointer to incomplete type
/root/audiofunc.c:1187: error: &#8216;VM_WRITE&#8217; undeclared (first use in this function)
/root/audiofunc.c:1187: error: (Each undeclared identifier is reported only once
/root/audiofunc.c:1187: error: for each function it appears in.)
/root/audiofunc.c:1191: error: dereferencing pointer to incomplete type
/root/audiofunc.c:1191: error: &#8216;VM_READ&#8217; undeclared (first use in this function)
/root/audiofunc.c:1199: error: dereferencing pointer to incomplete type
make[2]: *** [/root/audiofunc.o] Error 1
make[1]: *** [_module_/root] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [modules] Error 2


After seeing this, i followed the instructions and changed the variable KERNEL_SRC in the Makefile with the appropriate source, and also I followed the instructions and changed ORIG_FIRMWARE=1 and USE=LIRC=1 , and try to "make" it again. But still, same output.

I really don't know how to make my Creative Extigy work in Ubuntu :(

---

### Post by aefaradien on 2007-10-03
i get the same problem and i am wondering if perhaps i am missing some dependency required for compiling.  the install instructions are not very detailed but do say "you need a set of configured kernel sources".  can someone please tell me what this means?

---

### Post by wvrn on 2007-11-10
hi,
a hack did it for me (suse 10.3)

append the path to your (!) kernel-includes to the "CFLAGS" defined in the Makefile:
```
CFLAGS = -Wall -I/usr/src/linux-2.6.22.5-31/include/
```

in the sources (audiofunc.c, dma.c, remote.c) add the includes:
```
/*--------------------------------*/
#include <linux/mm.h>
#include <linux/page-flags.h>
/*--------------------------------*/
```

there are still warnings building the remote.ko, so i don't think the remote is working fine yet !

---

