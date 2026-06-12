---
title: "cpu architecture and ubuntu"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by seatea on 2005-11-16
I like the attempts of the  Ubuntu development team to be inclusive fof different computer  architectures. I have only used computers with a PowerPC processor which works well with the Ubuntu  PPC version with a few exceptions; Flash, RealPlayer,  and various add on programs. I have never  really understand how the processor and program code interact, but I have come to appreciate the  limitations of options typically available to PPC users. This was true when I was running just the Mac OS as well as with Ubuntu. Having always been in the Mac environment, I have been frequently advised of the superiority of the PowerPC compared to Intel processors. That may be true, but I am less enamored with PowerPC CPU use, especially in light of Apple's decision to start producing Intel based computers, than I was in the  past. Since my computer is slow by today's standards, I have  a G4 400 MHz and ripe for replacement, I am contemplating  switching to a different architecture. There seems to be a wide representation of processors in the forums and I hope to get a better understanding of the pros and cons of the available versions of processors from those users. The PC(Intel i86) phrase keeps showing up. What does  "i86" refer to in  processors? My understanding is that this version of the install CD will run on any Pentium or  Celeron chipset as well as AMD. The 64-bit PC(AMD 64) install  CD will only run on the AMD 64-bit computers, but the AMD 64-bit computer will run  either the PC(Intel i86) or the 64-bit PC(AMD 64). Is that correct?

While it is always great to have the fastest processor, in truth, I don't do any tasks that are very processor intensive. I do want a better quality product that will last without breaking the bank, my bank anyway. I would rather have a processor that runs cooler and more reliably than one that is faster and not as well supported. I have read a lot  of favorable  comments about  AMD and have seen a fair number of AMD users in  these  forums. Are AMD's processors better than Intel's Pentiums?

I would stay with the PowerPC based  computer and just upgrade  the processor in my computer to a faster one if there was good reason to continue using the PowerPC over the  long haul. Is there any justification with staying with this type of processor?

Thanks!

---

### Post by Kyral on 2005-11-16
Okay, lemme sort out questions.

PC by itself just means "Personal Computer". Hence PPC (Power PC)

"x86" refers to almost every 32 bit processor. This includes the VERY old i386 architecture all the way up to Intel's i686(Cellys and Pentiums) and AMD's K6 and K7(Durons and Athons) cores. They all get along, they just do things a little different (This is why there are seperate kernels for i686 and K7 in the repos, and also why the kernel for Ubuntu by default is i386. Any x86 will run them, but if you use the one for your core, it will run "better" on a low level sense)

"x86_64" is the proper, generic name for the 64 bit generation. AMD64 refers to the AMD line and IA64 refers to Intel's line. I don't have much experiance with 64 bit technology (Still running my good old AMD Athlon XP 2700+)

Now Intel or AMD? Thats a war that has been raging for a long time. Some people swear by Intel, other by AMD. AMDs have been known to overclock better than Intels, and also give more throughput. (Ever wonder why the Athlon XP/64 line is named like "2700"? Its because thats the "Intel" speed that the processor is equivelent to. So my Athlon XP 2700+ rated at 2.1 GHz has the same amount of power as an Intel running at 2.7 GHz.)

I hope this helps

---

### Post by seatea on 2005-11-16
[QUOTE=Kyral]Okay, lemme sort out questions.

"x86" refers to almost every 32 bit processor. This includes the VERY old i386 architecture all the way up to Intel's i686(Cellys and Pentiums) and AMD's K6 and K7(Durons and Athons) cores. They all get along, they just do things a little different (This is why there are seperate kernels for i686 and K7 in the repos, and also why the kernel for Ubuntu by default is i386. Any x86 will run them, but if you use the one for your core, it will run "better" on a low level sense)
[/QUOTE]

I appreciate the information. I  didn't notice an Ubuntu install CD for k7 or i686, but  you mentioned that there are separate kernels for them. Does the  repositiory  auto-detect the processor or is  there some  configuration change  that has to be made to  access  the  appropriate repository?

---

### Post by Kyral on 2005-11-16
Nah, there isn't a separate CD for them because it isn't needed. The x86 CD uses the i386 Kernel by default because it the "common denominator" in the x86 world. Anything that runs on i386 will run on the other variants in the x86 arch. However it tends to be slow.

You'd have to install the kernel by yourself, which is easy

For i686

```
sudo apt-get install linux-686
```

For i686 with SMP

```
sudo apt-get install linux-686-smp
```

For K7

```
sudo apt-get install linux-k7
```

---

### Post by seatea on 2005-11-16
I am very new to Linux, so please bear with me. I am surprised that it is so easy to change  the  kernel. I would have guessed that the volume  would have to be unmounted and an install disk used in order to change  the  kernel. You can change  the  kernel while it is in use?

---

### Post by az on 2005-11-17
It sounds worse than it is.

The kernel gets loaded into memory on boot.  It is a file with a bunch of corresponding modules (files) that are compatible to it.  The bootloader (grub) it told which kernel to load at boot.

Installing another kernel is done by installing another linux-image package.  This puts another linux image file on your hard drive, along with the original one.  You can have several.  That package also updates the bootloader to boot the new kernel by default.  So you will run your new kernel the next time you reboot.  You can still tell the booloader to load the older kernel, if the new kernel is wrong and won't boot.  It is very safe.  You can then remove the other kernel (or the new one, if it doesn't work)

There is a tool called kexec, which kernel devs can use to slam a new kernel into memory without rebooting, but that is not something you do without a helmet.  And it is only used to save time.

---

