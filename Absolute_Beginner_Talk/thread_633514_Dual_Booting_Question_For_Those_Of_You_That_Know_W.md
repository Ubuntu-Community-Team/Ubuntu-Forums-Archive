---
title: "Dual Booting Question For Those Of You That Know What You're Doing"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2007-12-06
Ok so i wanted to dual boot windows on my hard drive with my linux os but i guess that's not going to work because when i got my sony vaio laptop geek squad made me a one disk system restore and that's what it's good for i can't do the dual boot like that. So what i'm planning on doing is reinstalling windows vista to my computer and then adding ubuntu to the other half after windows is already installed. will that work arlight?

---

### Post by Happy_Man on 2007-12-06
It will work swimmingly... so long as you use Vista to free up space for a partition and not Gparted on the Ubuntu live CD. For help on doing this, see [http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/)

---

### Post by jba6511 on 2007-12-06
what I would do is use parition editor in the ubuntu live cd to partition some space, say 20 GB for vista, then another partition for ubuntu. Then install vista into the vista partition you just created and then install ubuntu into the ubuntu partition. GRUB will find the vista install and allow you to select which OS you want to boot into at startup.

---

### Post by MQMike on 2007-12-06
Dual boot Vista – The Definitive Guide:     [http://apcmag.com/dualboot](http://apcmag.com/dualboot)
(Vista with XP and/or Linux and/or all 3)

---

### Post by RadiationHazard on 2007-12-06
happy man yours seems pretty easy even for a huge comp noob such as myself. so after i make the vista smaller then what will i do?

---

### Post by RadiationHazard on 2007-12-06
ok and mqmike yours seems nice too. but it's for an older version on ubuntu will 7.10 work the same?

---

### Post by AvidChronos on 2007-12-06
If you decide not to reinstall before installing ubuntu, defrag first! otherwise you might lose some data.

Here is what I did:

I installed vista, because it likes to be first, and then deleted my 10 Gig system restore partition (Dell) and then created a new blank partition or NTFS and made it 10 gigs. After that I booted up the live cd and chose to use the 10 gig parition and let it do its thing. GRUB was installed as my bootloader so now I have ubuntu and vista successfully. Only problem is i need to remember how to give vista the default boot in grub....

---

### Post by MQMike on 2007-12-06
Yes, the how-to will work for 7.10 as well.

---

### Post by RadiationHazard on 2007-12-06
ok so for this site [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first) the picture that they show with it highlighted in blue? is that how much i'm supposed to shrink it by? I just reinstalled vista to my computer...:confused:

---

