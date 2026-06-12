---
title: "Ubuntu 7.10 Live CD problem..."
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by -Theanimal- on 2007-10-19
I wanted to try a linux distro to see what it really was, and Ubuntu looked like a good start:)
So i burned a cd with the new Gutsy Gibbon release, and booted it.
When i choose 'start or install', it loads the kernel and brings up another orange load bar.
Then it stops at the last block/bit, it just freezes:(
It does exactly the same with the safe boot option...
I already checked the discs Integrity and it was fine.

Hardware:
Asus M2NPV-VM
AMD Sempron 3200+ @ 2.35 Ghz
Ati Radeon X1950 pro
1 GB ram

Does anyone has a solution for this problem?
Thanks in advance:)

---

### Post by aJayRoo on 2007-10-19
I don't know how long you waited for Ubuntu to load but be aware that since it is loading an operating system into memory it can take a very long time. There are often periods of what seems like inactivity, a black screen or two etc. You need to be quite patient when working with a live cd. That said, it is possible that you were patient with it but it still does not load, in which case I'm afraid I probably can't be of much help.

 If you are wanting to try out Ubuntu without installing it then it might be worth downloading the 7.04 live CD, I know it isn't the newest version (only just, mind!) but it will give you a great impression of what Ubuntu is like to use. If at some point you decide you want to install Ubuntu to your hard drive then you can always download the alternate CD for version 7.10. The alternate version does not contain the live graphical environment that the live CD provides, however it should boot and allow you to sucessfully complete an installation. Good luck, I hope you enjoy using Ubuntu as much as I do.

---

### Post by FredB on 2007-10-19
> **-Theanimal- said:**
> I wanted to try a linux distro to see what it really was, and Ubuntu looked like a good start:)
So i burned a cd with the new Gutsy Gibbon release, and booted it.
When i choose 'start or install', it loads the kernel and brings up another orange load bar.
Then it stops at the last block/bit, it just freezes:(
It does exactly the same with the safe boot option...
I already checked the discs Integrity and it was fine.

Hardware:
Asus M2NPV-VM
AMD Sempron 3200+ @ 2.35 Ghz
Ati Radeon X1950 pro
1 GB ram

Does anyone has a solution for this problem?
Thanks in advance:)

Maybe because you overclocked your CPU ? Linux hates overclocked CPU.

Anyway, wait for 30 seconds, and see if the booting continues or not.

---

### Post by -Theanimal- on 2007-10-19
I waited for about 10 minutes to let it start;) Don't think it should take longer than that...
But i will downclock my CPU then and try it again:) Else i will try an 7.04 live cd

---

### Post by eldragon on 2007-10-19
follow this thread: [http://ubuntuforums.org/showthread.php?t=580020&page=8](http://ubuntuforums.org/showthread.php?t=580020&page=8)

---

### Post by cypry on 2007-10-19
I have exactly the same problem, but didn't overclock my CPU.

---

### Post by Frak on 2007-10-19
Did you burn it at the slowest speed possible?

---

### Post by -Theanimal- on 2007-10-19
The overclocked CPU seemed to be the problem:) It boots now!
Thanks for the help!

---

### Post by cypry on 2007-10-19
> **Frak said:**
> Did you burn it at the slowest speed possible?

I burnt it at 8x.
I tried now to remove quiet splash from the boot options. Everything works fine, until it writes
Loading gnome....
then it's suddenly freezing.

---

### Post by Frak on 2007-10-19
> **cypry said:**
> I burnt it at 8x.
I tried now to remove quiet splash from the boot options. Everything works fine, until it writes
Loading gnome....
then it's suddenly freezing.
Go for "Safe Graphics Mode"

---

### Post by timcredible on 2007-10-19
could be the ati card (the live cd doesn't have ati drivers).  try downloading the alternate cd, which will install in text mode, then you can install the ati driver.

---

### Post by cypry on 2007-10-19
I tried that too, and many other combination(with noapic, without noapic). None of them worked. It seems to stop randomly at some points(not only while loading gnome), then just freeze.
I'll try to re-download and burn a new copy.

---

### Post by Frak on 2007-10-19
Try the alternate disc and see if that solves your issue.

---

### Post by cypry on 2007-10-19
> **timcredible said:**
> could be the ati card (the live cd doesn't have ati drivers).  try downloading the alternate cd, which will install in text mode, then you can install the ati driver.

I have an NVIDIA GeForce Go 6100 graphics card.

---

### Post by cypry on 2007-10-19
> **Frak said:**
> Try the alternate disc and see if that solves your issue.

The alternate disk doesn't work either. The cd boots, i select the language, the country, the keyboard, then it starts to check the cd. It always stops there somewhere, at a variable percent. I don't get it.

---

### Post by Frak on 2007-10-19
> **cypry said:**
> The alternate disk doesn't work either. The cd boots, i select the language, the country, the keyboard, then it starts to check the cd. It always stops there somewhere, at a variable percent. I don't get it.
Are you using a CD-R or CD-RW?

---

### Post by rgraves22 on 2007-10-19
Completly unrelated, but I had a similar issue with Fedora, it didnt like my ATI X1300 in a dell gx280, 2GB of RAM. Removed the video card and booted up off of the internal video card, once the install was done, switched back over. It picked the video card up no problem... *shrug*

---

### Post by cypry on 2007-10-19
> **Frak said:**
> Are you using a CD-R or CD-RW?

A DVD-RW.

---

### Post by cypry on 2007-10-20
Still trying to install ubuntu 7.10 without success. I tried many times the live cd or the alternate cd, but the result is the same. At some random point, the CD stops spinning and everything freezes.

---

### Post by Frak on 2007-10-20
> **cypry said:**
> Still trying to install ubuntu 7.10 without success. I tried many times the live cd or the alternate cd, but the result is the same. At some random point, the CD stops spinning and everything freezes.
Do a RAM (Memtest) test to make sure you aren't segfaulting.

---

### Post by cypry on 2007-10-21
> **Frak said:**
> Do a RAM (Memtest) test to make sure you aren't segfaulting.

I did, and my memory seems ok.

---

