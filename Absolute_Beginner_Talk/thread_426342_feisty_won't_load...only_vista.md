---
title: "feisty won't load...only vista"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by treeby on 2007-04-28
just got a new computer....core 2 duo, GeForce7600GT and msi mobo and a 500gig sata drive

i installed vista on the sata drive no problem and then used gparted to partition my drive like this:

/dev/sda1 80gig NFTS - vista
/dev/sda4 300gig FAT32 - for data
/dev/sda2 90gig - Feisty
and a swap in there, too

then i installed feisty..it installed in like 30 minutes with no problems.

in gparted when i change the boot flag from the vista partition to the Ubuntu partition and start up
it says there's no OS...when i put the boot flag on vista, vista just starts up. i get no grub menu.

i don't have a RAID set up...i don't even know what that is. i have two other IDE drives on master
and slave set to boot up after the SATA..i just want to use those for data.

any ideas how to get feisty running? it said it installed no problem....

thanks so much!

---

### Post by Mazza558 on 2007-04-28
> **treeby said:**
> just got a new computer....core 2 duo, GeForce7600GT and msi mobo and a 500gig sata drive

i installed vista on the sata drive no problem and then used gparted to partition my drive like this:

/dev/sda1 80gig NFTS - vista
/dev/sda4 300gig FAT32 - for data
/dev/sda2 90gig - Feisty
and a swap in there, too

then i installed feisty..it installed in like 30 minutes with no problems.

in gparted when i change the boot flag from the vista partition to the Ubuntu partition and start up
it says there's no OS...when i put the boot flag on vista, vista just starts up. i get no grub menu.

i don't have a RAID set up...i don't even know what that is. i have two other IDE drives on master
and slave set to boot up after the SATA..i just want to use those for data.

any ideas how to get feisty running? it said it installed no problem....

thanks so much!

Try reinstalling.

---

### Post by treeby on 2007-04-28
i tried reinstalling...no luck. 
i had EasyBCD installed with their grub menu...that comes up and when I choose something like "linux"
(it doesn't say Ubuntu) i select that and it has some error about windows bsd...even though i don't have
EasyBCD installed any more. how do you work that EasyBCD anyway? i couldn't figure it out at all...
that's why i uninstalled it.

---

### Post by Computer Guru on 2007-04-29
Can you provide more details than that?

I think you meant Windows **BCD**..
You have to reinstall EasyBCD, add a Linux entry, verify the file exists in X:\NST\nst_grub.mbr (the boot drive is X:\) and then reboot.

Detailed info: [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

