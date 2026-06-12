---
title: "Macbook 3,1 incorrect max ram, no 64 bit, very sad!"
date: 2010-10-31
forum: Apple Hardware Users
---

### Post by sha.goyjo on 2010-10-31
Hey all. I know that this is more of an Apple users problem, but as it's something that I've never run across before, I thought that I'd post it on the main forums and see if anybody had any idea WTF was going on.

So when I say that this is one problem, what I actually mean is that this is multiple problems. Problemma the 1st, I have put 4GB of ram into the machine, 2 pc-5300 sodimms (the machine's official max, although it can supposedly support six, in a 4,2 configuration). Any operating system booted on the machine insists that there is only 2GB of ram on the system, 1GB in each slot. That includes OSX, Windows 7 64 bit, and Ubuntu 10.10 32 bit.

The other problem (and this is the really annoying one) is that I cannot seem to boot 64 bit OS's natively. OSX refuses to boot in 64 bit mode, even with the 6 and 4 keys pressed, or config file changes made, or what have you. The 64 bit kernel simply will not go. Windows 7 64 bit will install from the CD, and as long as you boot from the CD and then skip the install prompt it will boot to the installed copy of windows. It will not boot without the CD in the drive. Ubuntu 10.10 64 bit will not boot. It sits at a prompt which says:

1.

2.

Choose CD boot method:

Ubuntu 10.10 32 bit will boot just fine.

Here are some more detailed system specs if that helps anybody.

Intel Core 2 Duo 2.00 GHZ
Intel gma x1300 graphics
4 GB pc 5300 sdram
80 GB hdd
64 bit EFI
Currently installed OSX 10.6.4, but that can change (and will as soon as I can get 64 bit ubuntu on here !)

Thanks for any help you can give.

---

### Post by sha.goyjo on 2010-11-02
I hate to bump this stuff, but seriously I've gotten no help from anybody.

---

### Post by apoth on 2010-11-02
Can you swap each stick of RAM into the other's slot, if you haven't tried it already?

I don't even have a shot in the dark on the 64-bit I'm afraid.

---

### Post by sha.goyjo on 2010-11-06
Been tried, utterly unsuccessful

---

### Post by JaS on 2011-08-20
[http://netkas.org/?p=189](http://netkas.org/?p=189)

Read this and it will solve your issue. The EFI on this macbook is 64 bit, but it is set to only boot in 32bit, a lock by apple. following this post on netkas blog will allow you to boot into 64bit mode in any os im thinking. tho in OS X the gfx card drivers are only 32 bit so you will have no gfx acceleration under 10.6/10.7. Good luck and hope it helps

---

