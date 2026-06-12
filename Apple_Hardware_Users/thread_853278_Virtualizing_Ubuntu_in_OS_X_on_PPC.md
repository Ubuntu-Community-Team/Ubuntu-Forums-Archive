---
title: "Virtualizing Ubuntu in OS X on PPC"
date: 2008-07-08
forum: Apple Hardware Users
---

### Post by dcjones on 2008-07-08
Is it possible to virtualize Ubuntu on PPC? I know it's possible on intel based macs but I can't seem to find a way to do it with PPC. 

My work computer is a PPC G5 and the IT department would not be happy with a dual boot setup. OSX can be very painful to use at times and it would be awesome if I could get Linux virtualized on it. 

thanks

---

### Post by owlgorithm on 2008-07-08
I used to use Microsoft Virtual PC, although I was running Windows XP and not specifically Linux. It should work with Linux, though.

Alternatively, are you familiar with fink and macports? You'll need the Developer Tools installed (which are included on the installation CD), but once you have those, these free package systems can install thousands of packages from binary or source. Then, you can run many (most?) of the same programs from Linux on Mac natively inside the X11 application. I have personally compiled KDE and Gnome, for instance, using Tiger on PowerPC. (It took a loooong time, though... use binaries!). Also, TeX Live, the GIMP, command line utilities, etc. are available. You can run your Mac very similarly to a Linux box at that point, when Mac becomes unbearable ;-)

One caveat is that X11 remains broken in many respects under Leopard, since they switched from xfree86 to xorg and broke a lot of things in xquartz. That said, I know for sure the setup with fink and macports works as described under Tiger. I would suggest, however, that you pick only one of the two.

---

