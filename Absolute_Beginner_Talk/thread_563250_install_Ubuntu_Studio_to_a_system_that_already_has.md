---
title: "install Ubuntu Studio to a system that already has Windoze p and Fedora 7 ?"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by crowds on 2007-09-29
Hi everybody.

Ok so I am dying to try out Ubuntu studio but after having to recently re install both windows and Fedora 7 I thought I would just check up on how to go about things and avoid any more tears.

I have Three drives with the primary drive containing both Windows XP * and Fedora 7 as a dual boot. I want to add U studio as a third os but It will need to go on a partition  on Drive No three (currently set as slave on the secondary IDE) as there is no room elsewhere. I have already created a 15 gig (for now)  Ext primary partition on the third drive ready to go but I am fearful of messing up my boot file and loosing all three os's.

Ideally I would like to have it as an option from Fedoras Grub along.
Is there anything I need to take into consideration before I go ahead and try things... what would be the most fool proof way to proceed, am I just being over cautious and should I just put the dik in and go for it ?

Crowds


*Need to keep hold of XP due to the nature of my work and the lack of a linux solution  for my aark 24 audio card :(

---

### Post by MobiusNZ on 2007-09-29
First up, backup!

Then, if you chuck the disk in and install, it should pick up your other installs quite happily and add itself to the grub (or replace it with it's own that has the other os's in... not too sure, I've only dualbooted with winblows, never another linux)

---

### Post by louieb on 2007-09-29
When it comes to the GRUB install part put the GRUB pointer not in the MBR but in the boot sector of The Ubuntu partition.  

Then you can modify Fedora's grub to chainload Ubuntu or or use the configfile option. Scroll down a ways on this page, it has all the information you need to set it uo. [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

IMHO absolutely the #1 and #1a way to dual boot multiple Linux installs,

---

### Post by crowds on 2007-09-30
Thanks to both of you for you help. It installed in completely the wrong place but lukily within existing free space :) and i installed grub on a floppy so i copy its settings over to the fedora grub and there is now three os's sitting next to each other happily :)

Thanks again.

Crowds

---

