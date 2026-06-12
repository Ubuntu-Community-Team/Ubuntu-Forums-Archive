---
title: "Freezes during Install of K-/Ubutu"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by molex on 2006-08-03
I posted this in the installation forum and got ignored So Im posting it here too.

Hi my computer is running the following(Obtained from PC WIZARD):
[b]
Mainboard : [http://www.abit.com.tw/](http://www.abit.com.tw/) GD8 (Intel i915-ICH6)
Chipset : Intel i915P
Processor : Intel Pentium 4 630 @ 3000 MHz
Physical Memory : 1024 MB (2 x 512 DDR-SDRAM )
Video Card : Nvidia Corp GeForce 6800 [NV41.1]
Hard Disk : SAMSUNG (160 GB) [WINDOWS XP Drive]
Hard Disk : Maxtor (82 GB)[THIS IS MY PLANNED LINUX DRIVE IT IS ON AN ATAPI CALLED ITE8211, it appears as hda1 in Linux]
DVD-Rom Drive : ASUS DVD-E616P2
DVD-Rom Drive : _NEC DVD_RW ND-3550A
DVD-Rom Drive : XC1205K LED489F SCSI CdRom Device[Fake emulated in Windows]
Monitor Type : Dell Computer DELL E171FP - 17 inchs
Network Card : Intel Corporation 82540EM Gigabit Ethernet Controller
Operating System : Microsoft Windows XP Home Edition 5.01.2600 Service Pack 2
DirectX : Version 9.0c (March 2006)
[/b]


When I go to install in Ubuntu or Kubuntu, first off I am only able to boot the kernel with ACPI=OFF otherwise it freezes at mounting the file system. Next the LiveCD boots fine and I click the install ICON and then choose to install on my 82GB Maxtor Drive. The formatting goes fine, but 41% into copying the Ubuntu files and 61% into installing the Kubuntu files the installer freezes. I have tried waiting it out and it remained frozen for hours on both. I also tried using the Alternative install but those of these give me "FAILED TO MOUNT CD-ROM DRIVE".

Is there a known reason for this? Is my setup not "Ubuntu ready" I've tried booting the alt install with my ATAPI disabled and still got the same error. Does god hate me? Will girls ever talk to me?
](*,) 
PEACE, and I appreciate the help to come

---

### Post by ironfistchamp on 2006-08-03
All I can say is that if you have burnt the disks yourself make sure you have burnt them at a speed no higher than 4x. If you do it higher it can cause probs. My friend was trying to install from a disk burnt at a higher speed and it froze up all over the place.

Also be wary of cross posting (same thread in multiple places). The mods don't like it :p 

hope this helps

Ironfistchamp

---

### Post by molex on 2006-08-03
First off...this forum>Installation forum thanks for not ignoring me.

I'm gonna reburn like you said

Im at work now. BUT I AM BOUNCING WITH GLEE!

---

### Post by ironfistchamp on 2006-08-03
Hope it works for you. No garuentee but is the first thing to get out of the way.

---

### Post by molex on 2006-08-03
Nope...still froze at %50...trying now with ITE8211 as primary boot controller...maybe thatll help

---

### Post by molex on 2006-08-03
Didn't help

It freezes everytime!!!

Its not bad RAM..cuz I ran the test.

Any ideas?

---

### Post by ironfistchamp on 2006-08-03
Sorry i am fresh out of ideas. Could be some incompatible hardware. I am not really one to know what is and isn't compatible though sorry.

---

