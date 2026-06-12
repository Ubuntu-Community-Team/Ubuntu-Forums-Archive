---
title: "New desktop PC compatibility check"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by chinaski on 2007-09-11
hi I am about to buy a new machine as my old one died yesterday

I have basically two possibilities:

Option 1:

• Processor: Intel Core 2 Duo E6550 - 2,33 GHz, FSB 1333 MHz, Cache 4 MB
• Motherboard: Asus P5LD2-X, Intel 945P, FSB 1066 MHz, 4xDDR2 667 Dual
Channel, Max 8xUSB 2,0
• RAM: 1 GB, V-DATA, DDR2 667, CL 5
• Hard Disk: 160 GB, Maxtor DiamondMax Plus 21, 2 MB Cache, SATA2
• DVD: LG GSA-H54N, Black OEM
• Video Card: Asus EN7200GS, NVIDIA 7200GS, 256 MB
• Audio: 6 canali SoundMax AD1986A Audio Codec 
• Network Card: Realtek Gigabit LAN

Option 2:

• Processor: AMD Sempron 3600+ - 2,00 GHz, FSB 1000 MHz, Cache 256
KB
• Motherboard: Asus M2N, NVIDIA nForce 430, FSB 1000 MHz, 4xDDR2 800
Dual Channel, Max 10xUSB 2,0
• RAM: 1 GB, V-DATA, DDR2 800, CL 5
• Hard Disk: 160 GB, Maxtor DiamondMax Plus 21, 2 MB Cache, SATA2
• DVD: LG GSA-H54N, Black OEM
• Video Card: Asus EN7200GS, NVIDIA 7200GS, 256 MB
• Audio: 6 canali SoundMax AD1986A Audio Codec integrata
• Network: Realtek Gigabit LAN, integrata

Do you think everything is supported in both options?

Could you point me out to a good and up to date hardware compatibility list?

I need a new machine asap and I have not many chances to check many sites/forums to find info myself because I have no other PC or notebook to use at home, so any help would be greatly appreciated

---

### Post by LowSky on 2007-09-11
i dont see any issues, the nvidia card should work as long as you know what your doing

---

### Post by mcduck on 2007-09-11
The one with Core 2 Duo will have huge performance benefit over the Sempron one. If those 2 are your options I wouldn't consider the Sempron machine even for half a second :D

Seriously, those setups are from 2 different planets.

Anyway, I suppose the hardware in both setups should work fine with Ubuntu. So just get the first one..

---

### Post by mlentink on 2007-09-11
+1 Core 2 dUO...

---

### Post by n3tfury on 2007-09-11
> **mlentink said:**
> +1 Core 2 dUO...

^

---

### Post by chinaski on 2007-09-11
thank you all

I'll definitely go for the Intel one ;)

---

### Post by chinaski on 2007-09-12
*update*
 
I was thinking about changing the motherboard (option 1) with a Asus P5K/SE because of the FSB 1333 MHz which match perfectly the processor, but I cannot find any relevant info on chipset compatibility
 
do you know if it's a good choice?
 
Asus P5K/SE Intel P35

---

### Post by rileyrg on 2007-09-12
It works fine with Ubuntu Feisty, not with Debian Etch stable. However, this is with a SATA DVD drive and not an IDE one. No releases currently recognise the onboard IDE controller.

---

### Post by chinaski on 2007-09-12
so it's like being without DVD drive, or I am misunderstanding what you are saying?

EDIT: I realised only now what you meant :D

I'll go for that mobo with a SATA DVD Drive then, thanks a lot ;)

---

### Post by rileyrg on 2007-09-14
Another bad thing is that you must put the SATA into "compatible" mode in the BIOS. In "enhanced"  the kernel boot freezes just after it mounts the root partition.

---

### Post by chinaski on 2007-09-21
ok, got my new machine :D

• Processor: Intel Core 2 Duo E6550 - 2,33 GHz, FSB 1333 MHz, Cache 4 MB
• Motherboard: Asus P5K/SE intel P35, FSB 1333 MHz, 4xDDR2 800 dual channel, 8xUSB 2,0
• RAM: 1 GB, V-DATA, DDR2 800, CL 5
• Hard Disk: 320 GB, Maxtor DiamondMax Plus 21, 4 MB Cache, SATA2
• DVD: SATA DVD/CD/R/RW
• Video Card: Asus EN7200GS, NVIDIA 7200GS, 256 MB
• Audio: 6 channel SoundMax AD1986A Audio Codec 
• Network Card: Realtek Gigabit LAN

as far I can see with Feisty everything works fine out of the box

no need to set anything up in the bios

thanks to all again

later tonight I'll post in the hardware configuration thread ;)

---

