---
title: "When should one upgrade a kernel?"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by BrumleyGap on 2007-09-07
I upgraded my kernel to to 2.6.20-16 and my modem driver no longer works. I went back to the previous kernel and all is fine. So, as a real newbie (2 mos.) I am wondering when is it advisable to upgrade a kernel? Should I wait until something I want to use requires it, or are there good reasons to always install the latest version?

---

### Post by rich.bradshaw on 2007-09-07
I upgrade always, never had problems.

Basically, you might as well wait till it does something you need. Some have security patches, but basically it's not really a problem.

Microsoft only release new kernels when they make a new version, so just using windows, you would have updated your kernel about 6 times since 1985...

---

### Post by dca on 2007-09-07
> **rich.bradshaw said:**
> I upgrade always, never had problems.

Basically, you might as well wait till it does something you need. Some have security patches, but basically it's not really a problem.

Microsoft only release new kernels when they make a new version, so just using windows, you would have updated your kernel about 6 times since 1985...

Yes, what he said...
 
I have never upgraded a kernel as far as Ubuntu goes because of its six month release cycle which obviously contains an updated kernel...
 
Some kernel issues I've encountered was Fedora's default kernel does not work w/ ndiswrapper and my WiFi card causing lock-ups.  I got half-way through compiling an updated one and said, 'forget it'...  
 
Generally if you're on 6.06LTS Ubuntu, they're still developing security patches and fixes for that kernel (2.6.15.whatever I think) the newer one shows up in your updates...

---

### Post by BrendanM on 2007-09-07
The only reason I can think of not to upgrade is if you had to go to a lot of trouble custom compiling a driver for a piece of hardware, and that driver is compiled against a certain set of kernel headers. In that case, upgrading the kernel might break that driver.

Of course, there's also the chance that the upgraded kernel now includes support for your hardware "out of the box" so to speak.

So if you have unusual driver issues, I'd look before you leap on kernel upgrades.

---

### Post by LowSky on 2007-09-07
> **BrendanM said:**
> 
Of course, there's also the chance that the upgraded kernel now includes support for your hardware "out of the box" so to speak.

When I upgraded to .16 my wireless card just worked.. when before it didnt but i ddint care because i have a wired connection. i love updates.

---

### Post by Seisen on 2007-09-07
> **BrumleyGap said:**
> I upgraded my kernel to to 2.6.20-16 and my modem driver no longer works. I went back to the previous kernel and all is fine. So, as a real newbie (2 mos.) I am wondering when is it advisable to upgrade a kernel? Should I wait until something I want to use requires it, or are there good reasons to always install the latest version?

Generally, upgrading from one minor kernel release to the next won't bring any major differences. There are several reasons to upgrade the kernel. One is to take advantage of a specific new feature or driver; another is to be protected against a security vulnerability, or just to maintain an up-to-date and healthy system.

---

