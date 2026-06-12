---
title: "Windows on a PowerPC Ubuntu using QEMU?"
date: 2012-10-14
forum: Apple Hardware Users
---

### Post by canhoto on 2012-10-14
Hi.

Is it possible to run Windows on Ubuntu PowerPC using QEMU?

I looked for several guides on the net but that wasn't clear.

I installed several GUI's for QEMU and KVM (like Aqemu and Qemulator and some others). So, the process of creating virtual machines must be quite easy.

I also understand that I can install a virtual version of any Ubuntu or Power PC Linux with QEMU, for testing purposes, for instance.

The question is: can I installa Windows virtual machine on a Power PC Ubuntu (or any other Linux, of course), even if Windows is not made for Power PC? Or: can I run Windows on a Power PC Ubuntu? Or yet: can I run windows applications (without virtualizing the whole system) on a Power PC Ubuntu using QEMU or KVM (like the way Wine does it)?

Thank you for your help.

---

### Post by canhoto on 2013-02-15
> **canhoto said:**
> Hi.

Is it possible to run Windows on Ubuntu PowerPC using QEMU?

I looked for several guides on the net but that wasn't clear.

I installed several GUI's for QEMU and KVM (like Aqemu and Qemulator and some others). So, the process of creating virtual machines must be quite easy.

I also understand that I can install a virtual version of any Ubuntu or Power PC Linux with QEMU, for testing purposes, for instance.

The question is: can I installa Windows virtual machine on a Power PC Ubuntu (or any other Linux, of course), even if Windows is not made for Power PC? Or: can I run Windows on a Power PC Ubuntu? Or yet: can I run windows applications (without virtualizing the whole system) on a Power PC Ubuntu using QEMU or KVM (like the way Wine does it)?

Thank you for your help.


Well, I still didn't have an answer. Is there one? Please :(?

---

### Post by lubo2 on 2013-12-21
Stumbled onto this post looking for something else regarding Qemu and Ubuntu, and since I happen to know a bit about Macs and PowerPC, figured I'd reply. Too bad there were no other replies in over a year.

> [COLOR=#000000]*Is it possible to run Windows on Ubuntu PowerPC using QEMU?*[/COLOR]

Theoretically yes, so long as you can get qemu-system-i386 installed/running (the part of qemu that emulates an Intel/AMD compatible 32 bit CPU) and get it to recognize a Windows install CD/disk image (usually .iso format), or a .qcow format hard drive image file, though all of that will be slow, since you'd be emulating an x86 CPU on PowerPC. At best the same speed as Connectix Virtual PC, if not slower (Virtual PC had G4 Altivec optimizations which Qemu may lack). Only exception - certain versions of Windows NT (up to 4.0 I believe) had actual native PowerPC versions (very hard to find, and no I don't have it, I just know they existed) so the OS would run at native speed. Having said that, it presents two other caveats - lack of Windows apps for PowerPC (the x86 Windows programs will NOT run, only those that come with Windows for PowerPC, or ones recompiled for this purpose like Open Source software perhaps, Word, Photoshop, etc. are out of the question, being closed source) and how out of date NT 4 (or whatever the last PowerPC version) is - it was released prior to Windows 2000, so it's a 15 year old OS minimum.

> [COLOR=#000000]*I also understand that I can install a virtual version of any Ubuntu or Power PC Linux with QEMU, for testing purposes, for instance.*[/COLOR]
This is probably the best use for Qemu on PowerPC, to test another distro or newer version without wiping out your prior one, or perhaps to test one designed for ARM or another similar CPU, though that too may be pushing it, as with x86 above.

> [COLOR=#000000]*The question is: can I install a Windows virtual machine on a Power PC Ubuntu (or any other Linux, of course), even if Windows is not made for Power PC? Or: can I run Windows on a Power PC Ubuntu? Or yet: can I run windows applications (without virtualizing the whole system) on a Power PC Ubuntu using QEMU or KVM (like the way Wine does it)?*[/COLOR]

Unfortunately, so far as I know, aside from what I noted above, no. Windows/Qemu/PowerPC is likely to be slow, even if possible. Wine can run Windows apps without Windows itself, but it requires an x86 CPU, hence it would run on a MacBook but not a PowerPC Mac. Catch 22 I'm afraid.

---

### Post by xeno74 on 2013-12-23
> **canhoto said:**
> Well, I still didn't have an answer. Is there one? Please :(?

Yes, it's possible. :-)

[IMG]http://www.supertuxkart-amiga.de/amiga/debian7-x1000-qemu1.jpg[/IMG]


[IMG]http://www.supertuxkart-amiga.de/amiga/kernel-3.10.0-debian.jpg[/IMG]

[ATTACH=CONFIG]248830[/ATTACH]

QEMU threads for PowerPC computers:

[http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=1747](http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=1747)
[http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=1714&p=19901&hilit=QEMU#wrap](http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=1714&p=19901&hilit=QEMU#wrap)

---

### Post by xeno74 on 2013-12-23
> **canhoto said:**
> Hi.
I also understand that I can install a virtual version of any Ubuntu or Power PC Linux with QEMU, for testing purposes, for instance.


Yes, it's also possible. :-)

Lubuntu 13.10 PowerPC on QEMU.

[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=574[/IMG]

---

### Post by xeno74 on 2013-12-23
Windows NT 4.0 SP 6 has a good performance. Lubuntu PowerPC is very slow on QEMU. But SliTaz and Damm Small Linux both x86 have a good speed on QEMU.

SliTaz x86 on QEMU:

[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=659[/IMG]

Damm Small Linux x86 on QEMU:

[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=514[/IMG]

---

### Post by rsavage on 2013-12-23
Nice!

Have you got any notes on how to emulate Windows 98 that could be incorporated into the FAQ page?  There is a small section already, but it could really do with somebody who knows about this stuff writing some instructions [https://wiki.ubuntu.com/PowerPCFAQ#What_about_an_x86_emulator.3F](https://wiki.ubuntu.com/PowerPCFAQ#What_about_an_x86_emulator.3F)

p.s. is that lucid 10.04 you are running?

---

### Post by xeno74 on 2013-12-23
> **rsavage said:**
> Nice!

Have you got any notes on how to emulate Windows 98 that could be incorporated into the FAQ page?  There is a small section already, but it could really do with somebody who knows about this stuff writing some instructions [https://wiki.ubuntu.com/PowerPCFAQ#What_about_an_x86_emulator.3F](https://wiki.ubuntu.com/PowerPCFAQ#What_about_an_x86_emulator.3F)

p.s. is that lucid 10.04 you are running?

No, it's Debian Sid. Sorry I haven't any knowledge about Windows 98 on QEMU. Musa has installed Windows 98. If you have any questions, I can forward your questions to Musa. :)

---

### Post by xeno74 on 2014-05-20
Windows NT with the universal VESA/VBE video display driver on QEMU:

[IMG]http://www.supertuxkart-amiga.de/amiga/VBEMP_QEMU_WindowsNT_A1-X1000.jpg[/IMG]

---

### Post by luigiburdo on 2014-05-21
> **xeno74 said:**
> [COLOR=#000000]Damm Small Linux x86 on QEMU[/COLOR]



Christian great! is this Qemu 2.0 and  using kvm? because on my G5 Quad no kvm all systems report my emulated machine are with cpu 33mhz and i have 67 bogomips ... 
Means with kvm on my G5 probably i will reach more than 200 bogos good and speedy for use in fast way windows 98 and/or Me


Luigi

---

### Post by xeno74 on 2014-05-21
> **luigiburdo said:**
> Christian great! is this Qemu 2.0 and  using kvm? because on my G5 Quad no kvm all systems report my emulated machine are with cpu 33mhz and i have 67 bogomips ... 
Means with kvm on my G5 probably i will reach more than 200 bogos good and speedy for use in fast way windows 98 and/or Me


Luigi

It's QEMU 2.0 without KVM. Qemu-system-i386 doesn't support KVM on the PowerPC hardware. But my opinion is, that Windows NT is fast enough to work.

---

### Post by luigiburdo on 2014-05-22
Win 98 will be good too ;)
a pentium 100 mhz will be good for make old gaming or use old and good professional software of that time

---

