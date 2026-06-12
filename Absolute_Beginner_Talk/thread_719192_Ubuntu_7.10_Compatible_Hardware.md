---
title: "Ubuntu 7.10 Compatible Hardware"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by felix_d2008 on 2008-03-08
:) May I have your opinion and advice regarding these hardware I plan to purchase for a new Ubuntu System. My budget for this is around US$ 500. All of these would be purchased locally. The components are as follows:

Processor: Intel E2160 (1.8G) 1mb 800FSB PDC
Motherboard: Gigabyte GA-P31-DS3L PCIE/DualDDR/Lan/7.1Ch
Memory: Kingston 1GB PC5300 DDR2 667 (x2 for Dual Channel)
Video Card: Inno3D 8400GS 256ddr2 dvi 64bit
Hard Drive: Samsung 250gb 7200rpm SATA 3Gb/s
Optical Drive: Liteon DH-20A3S 20X DVD-RW SATA

Just want to know if there are any known issues with these and please provide the fixes or workarounds for these problems if you know them.

---

### Post by Rocket2DMn on 2008-03-08
Those look pretty good.  The only thing to catch my eye would be the "Inno3D 8400GS" video card.  It looks like a 3rd party nvidia card, so it should work.  Nvidia has good support in linux, though sometimes the restricted drivers can be annoying to install.  However, if it is a problem, we can troubleshoot it for you.

---

### Post by felix_d2008 on 2008-03-08
Thank you for your reply. I would also be grateful to those who would reply to this thread in the future. I read somewhere that using Automatix2 would simplify installing these restricted drivers.

---

### Post by Rocket2DMn on 2008-03-08
> **felix_d2008 said:**
> Thank you for your reply. I would also be grateful to those who would reply to this thread in the future. I read somewhere that using Automatix2 would simplify installing these restricted drivers.

NONONONONONONO!
NO!
Never speak that word around here again!  *Automatix* is like the devil incarnate, it has a very nasty habit of bricking systems, esp. during distribution version upgrade.  Once you install it, you're screwed.  Enough said on that topic.

Here is how you should approach installing restricted nvidia drivers: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
If that doesn't work, you can try it from the drivers on nvidia's website, but it's much more challenging.

---

### Post by felix_d2008 on 2008-03-08
Thanks for the heads-up on that one. I'm pretty sure I'm competent enough to follow those instructions. But if I do get stuck I will ask for help.

---

### Post by felix_d2008 on 2008-03-08
Please keep posting whatever opinions or advice comes to mind. Anything under the sun about Ubuntu and these hardware. Constructive criticism is more than welcome. It would all be highly appreciated. 

Processor: Intel E2160 (1.8G) 1mb 800FSB PDC
Motherboard: Gigabyte GA-P31-DS3L PCIE/DualDDR/Lan/7.1Ch
Memory: Kingston 1GB PC5300 DDR2 667 (x2 for Dual Channel)
Video Card: Inno3D 8400GS 256ddr2 dvi 64bit
Hard Drive: Samsung 250gb 7200rpm SATA 3Gb/s
Optical Drive: Liteon DH-20A3S 20X DVD-RW SATA

:popcorn:

---

### Post by daengbo on 2008-03-09
> **felix_d2008 said:**
> Please keep posting whatever opinions or advice comes to mind. Anything under the sun about Ubuntu and these hardware. Constructive criticism is more than welcome. It would all be highly appreciated. 

Processor: Intel E2160 (1.8G) 1mb 800FSB PDC
Motherboard: Gigabyte GA-P31-DS3L PCIE/DualDDR/Lan/7.1Ch
Memory: Kingston 1GB PC5300 DDR2 667 (x2 for Dual Channel)
Video Card: Inno3D 8400GS 256ddr2 dvi 64bit
Hard Drive: Samsung 250gb 7200rpm SATA 3Gb/s
Optical Drive: Liteon DH-20A3S 20X DVD-RW SATA

:popcorn:

Do you really need the NVidia card? Are you going to game (hehe) or do 3D production? If not, consider getting an on-board Intel graphics chip. The drivers are completely open and there are no stability problems. Also, if you ever DO have a stability problem with NVidia, no one will talk to you about it seriously until you disable the proprietary driver. You're better off using stock drivers that are in the kernel by default. Take the extra money and buy another 1GB of RAM. You'll be happy.

---

### Post by Rocket2DMn on 2008-03-09
> **daengbo said:**
> Do you really need the NVidia card? Are you going to game (hehe) or do 3D production? If not, consider getting an on-board Intel graphics chip. The drivers are completely open and there are no stability problems. Also, if you ever DO have a stability problem with NVidia, no one will talk to you about it seriously until you disable the proprietary driver. You're better off using stock drivers that are in the kernel by default. Take the extra money and buy another 1GB of RAM. You'll be happy.

Some intel cards (just like some nvidia and ati cards) don't support 3d accel and compiz in ubuntu, so that may not be the best idea.  Most are good, but you should research it first if this is the path you want to take.

---

### Post by felix_d2008 on 2008-03-09
What would you consider as an essential software and utilities for Ubuntu? Provide a top ten list if you can. Speaking of integrated graphic adapters. One of the mobos I looked into is the XFX nForce 630i with Integrated GeForce 7150 Graphics. Any thoughts on this particular chipset and mobo?

---

### Post by Mazza558 on 2008-03-09
> **felix_d2008 said:**
> What would you consider as an essential software and utilities for Ubuntu? Provide a top ten list if you can. Speaking of integrated graphic adapters. One of the mobos I looked into is the XFX nForce 630i with Integrated GeForce 7150 Graphics. Any thoughts on this particular chipset and mobo?

Generally speaking:

**Web browser = **
- Firefox or Opera (FF is installed by default)

**Music Player = **
- For simplicity - Exaile or Rhythmbox (Rhythmbox is installed by default)
- For more features - Amarok or Songbird
[B]
Office programs:[/B]
- General Office suite - OpenOffice (installed by default)
- Separate spreadsheet - Gnumeric
- Separate word processor - AbiWord
- Image Editor - GIMP (installed by default)
- Photo Organizer - F-Spot (installed) or Picasa from Google

---

### Post by felix_d2008 on 2008-03-09
Does anyone know if the Dell Inspiron Desktop 530N uses the Intel P31 Express Mobo Chipset? :confused:

---

