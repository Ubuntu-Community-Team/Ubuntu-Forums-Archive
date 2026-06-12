---
title: "64 bit Edgy on Macbook Core 2 duo?"
date: 2007-02-13
forum: Apple Intel Users
---

### Post by lamalex on 2007-02-13
Has anyone gotten 64-bit edgy running on their Core2Duo? If yes how did you do it?

---

### Post by das_syndrom on 2007-02-14
Hi!

The C2D Macbook has a new Atheros-wireless-chipset, which is not yet supported by madwifi. So you're forced to use ndiswrapper and AFAIK there are only 32bit-windoze-drivers available atm, so you need a 32bit system for ndiswrapper to work (correct med please if thats not true...).

So, unless the chipset is natively supported it makes no sense installing the 64bit-version. At least thats my opinion... :-)

Andi

---

### Post by RockoTDF on 2007-02-14
> **Iamalex said:**
> Has anyone gotten 64-bit edgy running on their Core2Duo? If yes how did you do it?

The "Core" CPUs are 32 bit x86 chips, so I think you're using the wrong install.

---

### Post by maxamillion on 2007-02-14
> **RockoTDF said:**
> The "Core" CPUs are 32 bit x86 chips, so I think you're using the wrong install.

If you would notice the original post said the [Core2]("http://en.wikipedia.org/wiki/Core_2") Duo, which is in fact a 64-bit (EM64T) processor which is fully [x86-64]("http://en.wikipedia.org/wiki/X86-64") compliant and should run the AMD64 release of ubuntu, I don't know exactly why anyone would have issues with its installation or "running" but then again I am unfortunately not in a financial state (ie - broke college student) to own such nice hardware so I can't really verify why or why not it would run.

Note: Even though this is Apple hardware, I don't know if Apple PPC is the appropriate place for this thread.

---

### Post by grazie on 2007-02-16
There's now a new forum, [Apple Intel Users]("http://www.ubuntuforums.org/forumdisplay.php?f=211"), for all topics regarding Apple Macs with Intel processors :)

---

### Post by lamalex on 2007-02-16
> **grazie said:**
> There's now a new forum, [Apple Intel Users]("http://www.ubuntuforums.org/forumdisplay.php?f=211"), for all topics regarding Apple Macs with Intel processors :)

yeah this was posted before that, and it has now been moved.

---

### Post by Gen2ly on 2007-02-17
I've read on the gentoo web site that MacBook owners are installing AMD64 versions for best perfomance of Gentoo.  So theoretically this is possible.

---

### Post by Thingi on 2007-02-17
You should have no problem installing the 64bit version on a c2d chip.

I'm currently running 64bit ubuntu on my mac mini......... :-) :-) I had previously upgraded the processor in it from a Plain CoreDuo to a 4mb cache Core2Duo 2.16Ghz :-)

If your EFI bit VTx bit is not enabled you will need to turn it on before you can successfully install any 64bit OS. The easiest way to do this is install parallels, create a vm and make sure the VTx checkbox is enabled. - this is a once only requirement 


thingi

---

### Post by incubus on 2007-02-17
I agree with das_syndrom.  Since the new Atheros wireless card is not supported, you need ndiswrapper.  But because there are only 32bit drivers, you won't be able to get it working on Ubuntu 64bit.

Keep an eye on this thread:
[http://madwifi.org/ticket/1001](http://madwifi.org/ticket/1001)

incubus

---

### Post by oskarloko on 2007-03-05
> If your EFI bit VTx bit is not enabled you will need to turn it on before you can successfully install any 64bit OS. 

¿ What's that ?

I'm shocked because I thougth CORE2DUO were 32bit processors... ( i think the two cores are 64bit... )

So, I'm using a triple booting of 32bits-system...  :oops: 

¿ Is very significative the improvement on a Pc ( mine is macbook ) between a 32bit and a 64bit OS ?

¿ Could it be very hard to install and completly setup a 64bits desktop ?

---

### Post by david_edmundson on 2007-03-12
It works fine. However as posted above (as yet) you can't get wireless working on 64-bit systems as it requires ndiswrapper (and there are no 64-bit windows wireless drivers).

---

