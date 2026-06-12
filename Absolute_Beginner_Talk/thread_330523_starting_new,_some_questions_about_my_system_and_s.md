---
title: "starting new, some questions about my system and sata controllers"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by maddogPT on 2007-01-03
hi all

I currently have a challenging task in hands (at least for me). After recently upgrading my system, now I want to install ubuntu on my system and make it dual boot with win xp.

My current system is:
OCZ Powerstream 420W
Abit AB9 pro
Pentium 4 3.0
DDR2 512MB Kingston
ASUS GForce 7100 GS
2x Western Digital Raptor 36g (RAID 0)
2x Western Digital Caviar 160G (RAID 1)
1 Western Digital Caviar 200G IDE
1 Maxtor 200G IDE

and the motherboard has 3 HDD controllers: jmicron (1 IDE + 2 sata), Intel ICHR8 (6 sata ports) and Silicon Image 3132 (2 sata ports).


Now the challenge. I'm a experienced windows user but new to linux. I want to buy a new HDD to install ubuntu but I have several questions:

1 - With my current system, wich HDD would you buy (sata or ide)?

2 - Which sata controller is best suported by Ubuntu?

3 - With my current specs, do you think it will be easy to find drivers? Do you think it will be easy to make the system run smoothly?

4 - Any other thing I should know forehand, any sugestions?

Thank you all in advance

---

### Post by bluefrog on 2007-01-03
if I have the money and the cardboard I buy SATA.

anyway, it's all your choice.

use ubuntu livecd and see if it finds your existing sata disks.

James

---

### Post by brad_p on 2007-01-03
i just installed Ubuntu with a Promise card with 2 drives attached. Formatting and partitioning was accomplished using GParted (disk format/partition tool)

i'm pretty new to Linux as well and i found GParted to be a great tool for disks.

after formatting and partitioning the drives with GParted, it was just a matter of locating the drives as devices and then mounting to the filesystem.

GParted is a LIveCD tool that can be used for most disk operations, ive found it to be very useful so far ...

brad_p

---

