---
title: "need some quick help dual boot"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Majestified on 2007-02-09
hey guys i have decided that i would like to try out ubuntu after giving the live cd a play with.

i have a 100 gig hd and i want to dual boot 

60gig is windows  around 35 is partitioned for ubuntu 

ok the problem:

i load the cd and double click on the install icon on the desktop 
every thing is fine but i need some clarification on the partitions 

ok i know i need a swap drive (set to 1gig)
i also have the root drive set to 20 gig 

i want to have a fat32 partition that i can swap stuff from windows to ubuntu and visa versa

it is currently set to 12 gig 

i clicked on next and it has sorted that the 1gig partition is for the swap and the 20 is the root

however i have the fat32 poartition and i dont know which option to use to mount it:

swap, / , /home, /boot, /usr, or /var

any help really appreciated guys. i also read that i should have seperate partitions for the root drive and the home drive is this true? if so what sizes do you suggest??

also if the sizes i have suggested are stupid please suggest others 


thanks :D

---

### Post by zvacet on 2007-02-09
I think 10GB for root is O.K.You want your home partition to be bigger,did´t you.In your place I will install Samba for folder sharing,and get more space to home partition.But,it´s up to you.

---

### Post by Majestified on 2007-02-09
i want to share between the os's on the one hard drive, samba is for networks isnt it? sorry if i worded that badly

---

### Post by Maestro23 on 2007-02-09
> **Majestified said:**
> i want to share between the os's on the one hard drive, samba is for networks isnt it? sorry if i worded that badly

Just make you a FAT32 partition to share the data between Window/Linux.

---

### Post by confused57 on 2007-02-09
> **Majestified said:**
> hey guys i have decided that i would like to try out ubuntu after giving the live cd a play with.

i have a 100 gig hd and i want to dual boot 

60gig is windows  around 35 is partitioned for ubuntu 

ok the problem:

i load the cd and double click on the install icon on the desktop 
every thing is fine but i need some clarification on the partitions 

ok i know i need a swap drive (set to 1gig)
i also have the root drive set to 20 gig 

i want to have a fat32 partition that i can swap stuff from windows to ubuntu and visa versa

it is currently set to 12 gig 

i clicked on next and it has sorted that the 1gig partition is for the swap and the 20 is the root

however i have the fat32 poartition and i dont know which option to use to mount it:

swap, / , /home, /boot, /usr, or /var

any help really appreciated guys. i also read that i should have seperate partitions for the root drive and the home drive is this true? if so what sizes do you suggest??

also if the sizes i have suggested are stupid please suggest others 


thanks :D

Since you're going to use the FAT32 partition for storage & sharing with Vista, you might want to reduce the root partition to something like 10-15 Gb & make the FAT32 partition larger.  The size of your root partition depends on how much you plan on downloading or installing to your home directory.
As far as a mount point for your FAT32, you might want to just type in something like "/media/data" where it asks for a mount point, formatted as FAT32.

---

