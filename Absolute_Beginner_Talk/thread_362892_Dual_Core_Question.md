---
title: "Dual Core Question"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Muppeteer on 2007-02-16
I just upgraded my cpu from an Athlon 3700+ to an X2 4400+ and i was wondering if i should need to do a kernel update or anything? I'm currently using 2.6.17.11 and it has picked up the cpu ok. I dunno if i'm imagining things but it seems to be running a bit slower...

Is there any specific kernel which works best for dual core? I have tried searching but can't find much useful...

Dunno if this is in the right section, but i consider myself a noob :)

---

### Post by ukripper on 2007-02-16
Are you using 64bit version ubuntu or 32bit?

---

### Post by Tomosaur on 2007-02-16
There is no specific kernel for dual-core processors - but you may get a performance increase from using the SMP kernel. It was renamed to 686-generic though. If that is the kernel you're using, then you may need to compile your own custom kernel with options to get the maximum performance. The generic Ubuntu kernels have a lot of stuff compiled in which you may not need. The reason this is done is to maximise compatibility - although the end result can be a performance drop.

---

### Post by Muppeteer on 2007-02-16
Thanks for the quick replies...

I'm using the 32 bit...Tried 64bit Suse about a year ago and it was soo crap...

I'll try updating the kernel then, what kind of options are you talking about? I've tried to install kernel 2.6.19.11 but couldn't get started up, think it's possible sata support...Guess i'll give it another go :)

---

### Post by Tomosaur on 2007-02-16
Options related to processing and I/O should be ones you'll need to think carefully about. Be sure to compile support for your filesystem **directly into the kernel** rather than as a module. You'll also need to compile bus (pci etc etc) support directly in too, or you may get an annoying kernel panic and you'll have to recompile all over again. Generally speaking - disable processor options for any brand other than Athlon. Some options will be 'generic', so you'll just have to decide whether you want them included or not. Also, find out whether you have a math co-processor or not, and select that option accordingly. You should also include SMP support and other such processor I/O options. You should us kconfig so that you get a nice, easy to use kernel configurator with explanations of the various options.

---

### Post by Arup on 2007-02-16
Try Ubuntu 64 on our core2d, I use it on my E6700 and it just simply flies as compared to its 32 bit version, you get to use full potential of your 64bit CPU. Also as per what it shows under Synaptic, the 686-smp kernel has been obsoleted by the generic SMP kernel so stick to generic.

---

