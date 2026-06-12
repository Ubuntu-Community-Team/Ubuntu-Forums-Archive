---
title: "Do PCI-cards from PC work in PPC under Linux?"
date: 2007-04-22
forum: Apple PPC Users
---

### Post by frafu on 2007-04-22
Hello, 

When a pci-card is compatible to linux, does this mean that it will work in both architectures (Intel/AMD and PPC under Linux?

Or can I only use pci cards that were designed for the Mac in a PowerMac under Linux? 

Thanks in advance.

---

### Post by stmiller on 2007-04-22
Yes, PC-only PCI cards will work in PPC or x86 Linux, as long as the pci card fits in the Mac slot okay. It's the same driver, in Linux.

---

### Post by frafu on 2007-04-23
Thanks for your answer. 

But when about the cards firmware? As far as I know, cards for a PPC have a different firmware as cards for a PC!? Does this not play any role? 

So I can use a pci graphics card for PC in my Powermac G3 beige!? 

Francesco

---

### Post by ssam on 2007-04-23
it might work.

i know that wireless cards that dont work with mac os x, work on powerpc ubuntu.

for graphics card be aware that the proprietary drivers tend to only have x86 versions

---

### Post by stmiller on 2007-04-23
> **ssam said:**
> 

for graphics card be aware that the proprietary drivers tend to only have x86 versions

There are graphics drivers for ppc linux, just as many as there are for x86 linux. The thing that ppc linux lacks is proper **3D** graphics drivers.

---

### Post by ssam on 2007-04-24
> **stmiller said:**
> There are graphics drivers for ppc linux, just as many as there are for x86 linux. The thing that ppc linux lacks is proper **3D** graphics drivers.

yes there are great opensource drivers for graphics cards, eg radeon for ati cards (what i use).

the opensource nv driver lacks 3d acceleration, but the nouveau driver (currently in developement) will have 3d

the opensource intel drivers are very good, but i dont think there are any powerpcs with intel graphcis chips.

but the proprietary drivers from ati and nvidia are x86 only

---

### Post by frafu on 2007-04-24
Thanks for pointing me to the fact that propriety drivers of pc-cards are only for x86. (Indeed, it sounds quite sensible to me.) 

Concerning the opensource drivers: restricting the discussion to nvidia and ati: I suppose that they can be compiled on both architectures (x86 and ppc)!? 

But what is the relation to the different firmwares between cards for a PC and a Mac?
Can I use a card in any architecture regardless of it being a PC or a Mac card when using opensource drivers? Does the firmware become irrelevant?

---

### Post by stmiller on 2007-04-24
Yes, in a nut shell: video drivers are there, and work in PPC Linux. The other person is making everything confusing.

The firmware thing should be a non-issue. If you have the machine and video card with you, just try putting it in, and booting up a live knoppix or Feisty CD and see if it works. Knoppix would pick it up. Then you would know that it works.

---

### Post by frafu on 2007-04-24
The question is rather intended for the case that I wanted to upgrade my old powermac. In fact, I wanted to know whether I could also pick the more cheaper pc hardware for the upgrade of a powermac. 

According to the replies here, it should be possible.

Moreover, can we generalise it to any hardware supported by linux: will supported hardware work under linux regardless of whether it was originally made for a pc or a powermac and regardless of whether it is plugged in a pc or a powermac?

---

### Post by didg on 2007-04-24
> **frafu said:**
> The question is rather intended for the case that I wanted to upgrade my old powermac. In fact, I wanted to know whether I could also pick the more cheaper pc hardware for the upgrade of a powermac. 

According to the replies here, it should be possible.


For the video card you have to try, Xorg has an x86 emulator for initialization but it seems to be broken on most PPC. 

> **frafu said:**
> Moreover, can we generalise it to any hardware supported by linux: will supported hardware work under linux regardless of whether it was originally made for a pc or a powermac and regardless of whether it is plugged in a pc or a powermac?


If there's no ROM and it works in Linux on x86, odds are good it will works on PPC. 

If the ROM is only for legacy BIOS support (like booting from a SCSI card) again it should work, I used Mac SCSI card on x86.

If the ROM is needed for initialization, like with most video cards, odds are it will not work.

---

### Post by frafu on 2007-04-24
@didg

Many thanks for your reply. 

Could you moreover please explain to me what you mean by "initialization" in this context? Especially, also about the emulator for inizilisation and the ROM ?

frafu

---

### Post by didg on 2007-04-25
Even if the graphic ship specs are known a lot of stuff is not disclosed and may change very quickly between card revisions, stuff like how you find memory size, set memory timing, how you ask the monitor its freqs range  and so on. 

As most consumer graphic cards haven't a full generic CPU they use the host computer CPU and software in ROM.  At boot time the host finds cards with ROM and executes their init routine.

Moreover this ROM implements legacy routines for BIOS and VESA output.

Even on x86 computers this init sequence may not be ran (when there's more than one graphic card), but the ROM software is real mode code so X still needs a small real mode x86 emulator for running ROM code in 32bits mode. 

This emulator is broken when run on a PowerPC and can't be used.

No bootstrap, no display :(

---

### Post by frafu on 2007-04-25
Thanks for explaining about the initialisation process. It is quite interesting. 

> **didg said:**
> 
Even on x86 computers this init sequence may not be ran (when there's more than one graphic card), but the ROM software is real mode code so X still needs a small real mode x86 emulator for running ROM code in 32bits mode. 


I now have problems with the quoted sentence, probably because I don't know what the "real mode" code is. 
Maybe you can also explain this to me. 

Many thanks.

---

