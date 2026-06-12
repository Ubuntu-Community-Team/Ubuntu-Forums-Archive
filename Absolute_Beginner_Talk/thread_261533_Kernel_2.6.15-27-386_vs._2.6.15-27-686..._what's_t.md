---
title: "Kernel 2.6.15-27-386 vs. 2.6.15-27-686... what's the difference?"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by vgeneral on 2006-09-20
I'm turning to the community for some advice on a kernel upgrade.  I'm currently using the 2.6.15-27-386 kernal on my P4 laptop and was wondering if it would be worth upgrading the kernel to the 686 version.  What do you all think?  Is it worth it?

---

### Post by insane_alien on 2006-09-20
the difference is the instruction set for the processor. 686 has a few tricks that the 386 doesn't. i'm assuming that you processor is running at a decent speed so you would not notice much difference in performance.

if your machine was a bit older then you would notice an improvement in performance but not so much with newer machines.

---

### Post by kick6 on 2006-09-20
definetly worth it!  The 386 kernel was designed to run on P1 and older systems, and doesn't have ANY of the later optimizations functional (SSE, MMX, etc.)  You should get a performance boost from using the 686 kernel.

EDIT: tooling around the desktop isn't going to make any difference, but if you do any kind of gaming or other processor-intensive stuff you'll pick up speed.

---

### Post by Metacarpal on 2006-09-20
I've read various threads debating whether or not the -686 kernel package makes that much of a difference.  Apparently, Ubuntu's been compiling the -386 kernel with most of the options for a lot of different processors already turned on.  I've also read reports that benchmark tests show little, if any difference between the two kernels...

That said, though... couldn't hurt to go to the -686 kernel and see for yourself.  Since you don't have to uninstall the -386 kernel to put the -686 one on, you can try switching between them at boot (using the GRUB menu) and running different programs to see which feels faster to you.

---

### Post by mostwanted on 2006-09-20
If your P4 has hyper threading, you'll almost certainly want the 686 kernel.

---

### Post by TheWalt on 2006-09-20
686 kernel also gave me multi-processor support.  This means if you have either more then 1 cpu, any chip with hyper threading (P4 or Xeon), or a new Intel Core Duo chip your only using half it's power on the 386 kernel.

---

### Post by vgeneral on 2006-09-20
Wow... thanks for all of the quick responses.  I think I'm going to take the plunge and upgrade my kernal to the 686 version...couldn't hurt, plus it may fix the issue of my laptop being unable activate the lock screen feature.  Anyway, the laptop running ubuntu will eventually be running the vmware server application, which will "theoretically" be my testing platform and from past experiences with that application, it can be a hog with resources.  So the upgrade will hopefully help with that piece.  

Again, thanks a bunch for all of your comments.

---

