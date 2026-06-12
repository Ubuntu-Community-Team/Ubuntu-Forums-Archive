---
title: "Mac OSx programs on linux"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by fb2007 on 2008-01-20
I've asked this question already on wine subforum (ubuntu forums), but I didn't get any answer. Is it possible to run mac osx programs on ubuntu linux?

---

### Post by Ub1476 on 2008-01-20
No, but a virtualbox might work. What programs were you thinking of?

---

### Post by fb2007 on 2008-01-20
No i was thinking more like wine. I know that Ms Office 2007 doesn't work in wine, but maybe Ms Office 2008 for mac would (work in a program like wine, for emulating mac osx if existed).

---

### Post by Paulmd on 2008-01-20
> **fb2007 said:**
> No i was thinking more like wine. I know that Ms Office 2007 doesn't work in wine, but maybe Ms Office 2008 for mac would (work in a program like wine, for emulating mac osx if existed).

Best I've found so far. I know you want a wine-type app, but one doesn't seem to exist. I've found some VMs.

[http://pearpc.sourceforge.net/about.html](http://pearpc.sourceforge.net/about.html)
[http://mac-on-linux.sourceforge.net/](http://mac-on-linux.sourceforge.net/)



See here for a lengthly discussion.

[http://linuxrevolution.blogspot.com/2006/02/mac-apps-on-linux.html](http://linuxrevolution.blogspot.com/2006/02/mac-apps-on-linux.html)

---

### Post by SOULRiDER on 2008-01-20
I believe you can use sheepshaver for that. I dont really know, since i have never sued it, i have however written a guide on how to compile it.

---

### Post by Ludford on 2008-01-20
Would it not be easier to get OSX programs to run on Linux than windows programs. OSX is basically a Linux distro isn't it?

---

### Post by Hallvor on 2008-01-20
> **Ludford said:**
> Would it not be easier to get OSX programs to run on Linux than windows programs. OSX is basically a Linux distro isn't it?

Mac OSX does not use the Linux kernel, so it is obviously not Linux. Mac OSX uses the Mach kernel.

[http://en.wikipedia.org/wiki/Mach_kernel](http://en.wikipedia.org/wiki/Mach_kernel)

---

### Post by Steveway on 2008-01-20
MacOSX uses a Frankenstein-Mach-BSD Kernel.
Even though it is a Unix-derivate it uses some propetiary toolkits etc for all it's programs.
Before we can even think about making a wine for MacOSX we need to rewrite Cocoa, Quartz and whatever they also use.

---

### Post by coolen on 2008-01-20
OSX isn't a Linux distro, but they're both Unix based (I believe the Mac kernel was originally forked from a BSD kernel...correct me if I'm wrong).

So, in theory, it may be easier to do this. I don't see why it'd be more difficult than Windows.

---

### Post by Paulmd on 2008-01-20
> **SOULRiDER said:**
> I believe you can use sheepshaver for that. I dont really know, since i have never sued it, i have however written a guide on how to compile it.

It's only for Os 9 apps and earlier.

[http://sheepshaver.cebix.net/](http://sheepshaver.cebix.net/)

---

### Post by rosegarden78 on 2008-01-20
It's my understanding you need a virtual computer like VMware and an original MacOSX installation.  Even WINE won't work without Common Files.  So you still need the original discs so far.  So you want Mac on a Linux try this:

[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

---

