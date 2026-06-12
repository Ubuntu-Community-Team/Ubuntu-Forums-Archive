---
title: "[SOLVED] Feisty Bug 8254"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by ashmew2 on 2007-04-28
Hi every1
I just bought a new system with the following configuration :

ASUS M2N4-SLI 
AMD ATHLON 64 Bit X2 3800+ 
Nvidia GeForce 7300 GT w/ 512 MB DDR2 RAM
1 GB DDR2 RAM
SATA HARD DRIVE (250 X 2)
LG CD/DVD WRITER

I have been using Edgy for quite some time and so i decided to try feisty. I burned it to a cd but as soon as i boot it and press enter on "Start or Install Ubuntu"  , It gives me an error  , something like :

MP-BIOS bug: 8254 timer not connected to IO-APIC. Try the apic=debug command and post report. Then try the noapic command.

If i try the apic = debug , it gives me the same error. But if i use the "noapic" command , it doesnt give that error , reaches loading screen , freezes for about 1.5 minutes (when the bar's loading) , and then it boots. But it does not detect anything , no sound , no router , no hard drive even. 

So what am i supposed to do ??
I really need to get Feisty Working.!!

PS - I dont have any problems with Dapper 6.06 (i used the 32 bit cd)
        I encountered the same APIC problem when i tried edgy 32 bit cd but if i use the alternate cd for installing edgy , it freezes when making the / patition at 64%.
!!
Thanks!!

---

### Post by Najand on 2007-04-28
Do you have the same result using 32 bit feisty?

---

### Post by ashmew2 on 2007-04-28
What do u mean ?  I havent tried using 64 bit Feisty. Ive only tried using 32 bit feisty so far as ive heard that compatibility issues occur in 64 bit!!

---

### Post by ashmew2 on 2007-04-29
bump....i really  need to know how to get feisty up and running...even if i boot it with the noapci option , is there any way to get all my peripherals working???

---

### Post by ashmew2 on 2007-05-02
Got it working after hours of frustration and no help :((....
Just pressed f6 and removed the "quiet" from the command and it booted fine..

Thanks neways

---

### Post by slacker9876 on 2007-08-04
Yeah, I just built off this motherboard and I too have the "MP-BIOS ... 8254" error. I used the 64-bit version since I could not boot the 32-bit CD and wanted to be 64-bit ready since this will be my primary computer. I have no audio, despite the fact the the ALSA drivers were included, if I get past it I'll post here but I may just disable the on board audio and put my creative SB card in there. 

Automatix sure was nice to get a lot of the 64-bit binaries installed and configured for the "package candy.

---

### Post by ashmew2 on 2008-02-13
Well removing quiet from the boot options doesnt show that error. As well as booting into recovery mode and starting GDM from there also prevents it.

---

