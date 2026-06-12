---
title: "max ram in 32bit ubuntu"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-04-17
So I have read conflicting reports, some people say that 3gb is the max ram you can have with 32 bit windows. Others say it is 3.5gb, and finally some people say that you can have up to 4 gb of ram.

Which is it?

---

### Post by tszanon on 2008-04-17
Absolutely, 4GB. But some of it will be used by the system, by BIOS, and whatever. The available memory reported by the system may vary.

---

### Post by meborc on 2008-04-17
depends on your video card for example... if your videocard uses your ram as well... but not over 4 gig

---

### Post by kpkeerthi on 2008-04-17
4 gb absolutely. There was a kernel bug (32-bit) that prevented it from seeing 4 full GBs. But that has been patched long back. Enjoy your RAM.

---

### Post by philinux on 2008-04-17
If you got a 1gig graphics card and 4 gig ram then the system can only use 3 gig of it so you wasted your cash.

---

### Post by kpkeerthi on 2008-04-17
> **philinux said:**
> If you got a 1gig graphics card and 4 gig ram then the system can only use 3 gig of it so you wasted your cash.

but most video cards have dedicated RAM. don't they?

---

### Post by mbadawi23 on 2008-04-17
> **tszanon said:**
> Absolutely, 4GB. But some of it will be used by the system, by BIOS, and whatever. The available memory reported by the system may vary.

Yes, the max is 4GB of RAM for 32bit systems. But I don't think that BIOS usually consumes any of it.
BOIS usually independent of CPU resources.

In the other hand, if you have an integrated mother board that has Audio chip and a Video chipset and maybe a network adapter, etc. all these modules may reserve chunks of memory for there use. And the biggest hawg is the video chipset (i.e. nVidia).

---

### Post by philinux on 2008-04-17
> but most video cards have dedicated RAM. don't they?

Makes no difference in this scenario this system has to address it.

---

### Post by mbadawi23 on 2008-04-17
> **kpkeerthi said:**
> but most video cards have dedicated RAM. don't they?

That is true. if the it is on a SEPARATE card gets plugged into PCI, PCI Express,  AGP, etc.

---

### Post by mbadawi23 on 2008-04-17
> **philinux said:**
> Makes no difference in this scenario this system has to address it.

No, the memory installed on the video CARD is only addressed by the GPU (Graphics Processing Unit) and the main CPU don't see it.

---

### Post by Joeb454 on 2008-04-17
Graphics Cards have dedicated VRAM (Video RAM).

32 Bit systems tend to see 3.25GB of RAM, just because of the limitations of 32 bit memory addressing on modern operating systems. Servers have different kernels and can see up to 64GB on a 32 bit OS.

With Linux however, you can in fact recompile your 32 bit kernel to see and use more than 4GB of RAM.

Now are we all clear on that? :D

---

### Post by kpkeerthi on 2008-04-17
> **mbadawi23 said:**
> No, the memory installed on the video CARD is only addressed by the GPU (Graphics Processing Unit) and the main CPU don't see it.

Exactly. My nvidia has 256 mb dedicated RAM. I have 2 GB RAM on board and my kernel can see it. All of it (2 GB)

If your graphics card uses shared memory, I agree, part of it will NOT be made available to the CPU.

---

### Post by philinux on 2008-04-17
It's true the video card has it's own ram, but the problem comes when the pc want to access that memory location on the video card. It needs to address it directly. If the total address space of the pc is 4gig, then the video card addresses must lie within that 4gig block. This only applies if you have 4gig installed ram.

---

### Post by mbadawi23 on 2008-04-17
> **philinux said:**
> It's true the video card has it's own ram, but the problem comes when the pc want to access that memory location on the video card. It needs to address it directly. If the total address space of the pc is 4gig, then the video card addresses must lie within that 4gig block. This only applies if you have 4gig installed ram.

I think that RAM on any separate module other than the mother board is privately addressed by its owner processor. The Main CPU never wants to address this RAM.

In the other hand different modules communicate to the CPU using a common interfaces which all are standards that manufacturers.

---

### Post by philinux on 2008-04-17
[http://www.dansdata.com/askdan00015.htm](http://www.dansdata.com/askdan00015.htm)

---

### Post by neurostu on 2008-04-17
So If I upgrade to 4gb of ram, will I will need to upgarde to 64 bit to get all 4gb of ram? i have a nvidia quadro 140m  (not sure how much on board ram). How much ram will I see with 32 bit and how much will I see with 64 bit? 


Also for the most part I know that 4gb is too much for the average user, however, I am doing a lot of matlab work and frequently open 800mb files in matlab.  In my case I feel that more ram will improve performance in these situations.  But seeing as how I don't spend 100% of my time using large chunks of ram will the upgrade from 32 to 64 bit really be worth it?

---

### Post by philinux on 2008-04-17
> A 32bit OS only has 4GB of address space, and some of that has to be used to address all the hardware in the computer (CPU, GPU, HDD, Ethernet, USB, etc). Anything that does not get an address cannot be used, no matter what state you live in or what BIOS settings you try.

You need a 64bit OS to use that last bit of RAM.

From the admin guy here scroll down.

[http://forum.notebookreview.com/showthread.php?t=207831](http://forum.notebookreview.com/showthread.php?t=207831)

---

### Post by ByteJuggler on 2008-04-17
> **mbadawi23 said:**
> No, the memory installed on the video CARD is only addressed by the GPU (Graphics Processing Unit) and the main CPU don't see it.

Not exactly true - you still have to transfer e.g. textures and data to the video card.  This is typically done with MMIO (Memory mapped IO.)  Which has to be mapped somewhere in the 4GB address space, making it not usable by the system.  If the entire video texture memory is mapped into the CPU address space, then your usable memory will be reduced by the size of the video card's memory, as another poster said.  (If the window used for transfers is smaller, then the "memory loss" will obviously be less. )

---

### Post by sayakb on 2008-04-17
I have a desktop with a 768MB GPU and 2*2GB DDR3 RAMs. The system shows 3800MB memory with an amd64 Gutsy.

---

### Post by ByteJuggler on 2008-04-17
> **mbadawi23 said:**
> I think that RAM on any separate module other than the mother board is privately addressed by its owner processor. The Main CPU never wants to address this RAM.

In the other hand different modules communicate to the CPU using a common interfaces which all are standards that manufacturers.

They often use MMIO (memory mapped IO)  [Read up ]("http://en.wikipedia.org/wiki/Memory-mapped_IO")about it...

---

### Post by ByteJuggler on 2008-04-17
> **neurostu said:**
> So If I upgrade to 4gb of ram, will I will need to upgarde to 64 bit to get all 4gb of ram? i have a nvidia quadro 140m  (not sure how much on board ram). How much ram will I see with 32 bit and how much will I see with 64 bit? 

It is impossible to know exactly how much RAM you'll see without knowing what devices you have in your system. (and even then it will take a bit of figuring out...)  But anyway to be able to use all 4GB of RAM you'll need a 64bit OS, yes.  Most machines have about 3.5GB out of 4GB on a 32bit OS, but it does vary.

---

### Post by kpkeerthi on 2008-04-17
> **philinux said:**
> [http://www.dansdata.com/askdan00015.htm](http://www.dansdata.com/askdan00015.htm)

Thanks for posting that link. One more myth busted. LOL!

---

