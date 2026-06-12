---
title: "ASUS 990fx Ubuntu 11.04 install problems"
date: 2011-09-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by nekrophiliac on 2011-09-27
The registration question was.  What is 1+1?  Kind of ambiguous i thought......but moving right along.....


I am a total Linux nooblet, I loaded it up so I could start to learn how to use it.  I successfully loaded Ubuntu 11.04 on a secondary HDD and have had it for several months.  Recently my Asus 880 decided to die on me after just 8 months of use.  I just bought a 990fx to replace it and I can no longer get Ubuntu to run.
     Grub loads perfectly and I can choose memtest, linux, or, Win 7.  Memtest and Win 7 work just fine.  Ubuntu however loads up to a crazy pix-elated screen and never brings up the log in menu.  I try to run the repair utility on grub with no changes.  I also tried to reinstall Ubuntu with a live CD, DVD, and USB stick, all with the same results.  It loads up a bunch of text about the kernel.

I wish I could copy paste it for yall to see but I can't get the KB to work at that point.

But basically it says Unable to handle kernel null pointer dereferenced at 00000000000010 

I then took the HDD to a different machine and loaded Ubuntu up with the usb flash drive and it installed flawlessly.  I threw that HDD back in my machine and the same thing happens, it loads up Ubuntu to some pix-elated screen and never allows me to log in.

Formatted or not, none of my install methods allow me to install Ubuntu on this machine.  The only change to my machine is the motherboard I went from a ASUS M4A88TD-V evo/usb3 to this ASUS Sabertooth 990fx.  All I can think of is it is a problem with the 990 chipset that didn't exist on the 880 chipset.  Or I got a bogus Mobo.....any help is appreciated.
.
AMD Phenom II X6 1055T
ASUS Sabertooth 990 fx
2x Nvidia 450 gts SLI
Antec 850 W
WD 1TB with Win 7 x64
HItachi 1TB with Ubuntu 11.04 x64

---

### Post by jdog59 on 2011-09-29
Hey [nekrophiliac]("http://ubuntuforums.org/member.php?u=1452312") I don't have an answer for you, but I just wanted to let you know your not alone. I have an Asus M5A97EVO and I was unable to complete a successful install, all I get are Horizontal Bars, and never get any further. I really want to try Linux but am a little leery. Hope you have better luck than I did...

---

### Post by aceraspire3000 on 2011-10-20
it's simple it's the lan driver i am looking for a fix and when i do i'll return to tell
:KS

---

### Post by aaronsegura on 2011-10-21
Same problem here.  Couldn't get past the first few seconds of kernel initialization with standard 64-bit 11.10.  Looks like the message right before it dies is a stack trace for the nouveau module.  I was able to get 11.10 installed by using the Alternative (text-based) Installer.

ASUS Sabretooth 990FX
AMD FX-6100 AM3+
G.Skill DDR3-1866 x8G
EVGA GTX550 Ti (Nvidia)

---

### Post by tristan8276 on 2012-03-25
Hi,

I'm building a new system with the 990fx and the AMD 8150 processor.  I wanted to install the latest Ubuntu build, but I didn't see anywhere if this install issue had been resolved?

---

