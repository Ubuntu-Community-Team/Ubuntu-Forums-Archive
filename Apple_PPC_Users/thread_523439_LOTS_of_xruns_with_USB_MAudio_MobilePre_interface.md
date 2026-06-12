---
title: "LOTS of xruns with USB MAudio MobilePre interface"
date: 2007-08-11
forum: Apple PPC Users
---

### Post by skipkent on 2007-08-11
I'm running Feisty on an old g3 imac, and my MAudio MobilePre usb sound device is detected fine but gushes xruns when I run it with Jack.  Any audio generated through it sounds 'crushed' and garbled.

Has anyone run into this?  I'm not running the low latency kernel yet, as the Ubuntu Studio site seems to be down.

Once again, the card is detected okay, but the sound/xruns is horrible.

Thanks,

-skent

---

### Post by skipkent on 2007-08-11
I seem to have solved this for the time being by setting the latency ridiculously high.  Workable for now, but if anyone has anything to add I'm all ears!

The same thing happens when I try to lower the latency on the built-in mac card too, so it's not just the mobilepre.

thanks,

-skent

---

### Post by stmiller on 2007-08-12
In qjackctl, check

force 16bit
soft mode

and set
Frames/Period to 64
(That latency setting should work)

The latency thing is possibly because of the stock non-audio friendly Linux kernel. So you'll want to get a low-latency kernel.

And btw Ubuntu Studio is currently ONLY for x86 machines. For PowerPC you'll have to compile your own low-latency kernel. It's not as terrifying as it sounds. If you can edit a text file, you can do it. Check out the PowerPCFAQ for a method to compile a kernel:

---

