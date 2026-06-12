---
title: "Problems w/ Keyspan USB serial adapter"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by djtopper on 2008-03-19
Hi folks,

I've checked the online docs and nothing seems to be working.  Here's the basic deal.  I have one of those Keyspan USB to serial converters (19HS to be specific).  It worked fine, pretty much out of the box IIRC on my older Ubuntu 6.0.61 LTS system.  Here's lsmod from that system:

lsmod | grep keyspan
keyspan                30644  1
usbserial              31336  3 keyspan
usbcore               130820  5 keyspan,usbserial,ehci_hcd,uhci_hcd 

and I of course have a nice /dev/ttyUSB0 on the box too.  Minicom talks to my little Keyspan adapter perfectly well.

But on my newer 7.10 install, I can't seem to get the thing working.  Doing "lsmod" shows nothing.  In fact, there doesn't even seem to be a driver named "keyspan" on the new 7.10 install.  Did they get rid of it?  What has changed in the last year or so?

So I'm a bit at a loss.  I'm a former Slackware user so am no stranger to recompiling my kernel, but it seems a bit more convoluted (maybe just different) under Ubuntu.  Besides, I didn't have to recompile anything under 6.0.61 LTS.  I don't even think I have the kernel sources on that box.

Regardless, even after doing a "make config" on my new 7.10 box (I do see a module for the keyspan cards, it's just not checked by default), I get the following error when trying to compile.

 make
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[1]: *** No rule to make target `arch/i386/kernel/asm-offsets.c', needed by `arch/i386/kernel/asm-offsets.s'.  Stop.
make: *** [prepare0] Error 2

so I'm obviously missing something.  I was hoping to just "make modules" and be done with it.  But unfortunately, that generates the same error of course.

Advice / input appreciated.

Thanks,

DT

---

### Post by djtopper on 2008-03-19
As I suspected, support *was* taken out in 7.10.  Thankfully,  Denis Lemire has already worked on and solved the problem:

[http://www.denis.lemire.name/2007/10/19/ubuntu-keyspan/](http://www.denis.lemire.name/2007/10/19/ubuntu-keyspan/)

DT

---

