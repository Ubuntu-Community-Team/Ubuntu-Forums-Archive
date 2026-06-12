---
title: "my feisty takes too long to kickup"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by amonrath on 2007-09-30
my old system has a "initio sata  raid card" which has it's own bios with two sata's hookedup to it, my feisty takes 8 minutes to runup and since i'm not that bright on linux is there a device detect and install utillity as i thought feisty being smaller it would be faster than my microsofts it was abit of a #$%&*#@ to get all the os's to sit beside each other as i've never tried triple boot but i found that Xp 1st then Vista  then linux as vista's bootloader wouldn't pickup ubuntu on my old girl so i've got two bootloaders to go thru but it works sweet ive managed to get beryl to work and found my old girl pushes it along sweet,is their a better g-card for my k7 msi 6450 m-board it's got a ati radeon 9550 agp,yeah i know it's an oldie but i get a kick out of pushing it along harder n harder can anyone help please?:lolflag:

---

### Post by amonrath on 2007-09-30
um can someone please tell me whats the best fireall/adware/antivirus to pull down please?

---

### Post by laidback on 2007-09-30
My boots up into Feisty takes 60secs. I'm using an IDE drive. See below for specs.

I don't use additional Antivirus anymore following info from this forum. But if you want one I would choose ClamAV which is available from the repositories. 

Firewall is via iptables and is installed by default in Ubuntu. If you wish to adjust then rules etc you could use Firestarter, again from the repositories. 

Adware blocking: if I remember correctly I set this up within Firefox, but I don't have any notes, my mistake sorry.

There are info pages on these items within Ubuntu help pages and wiki. Try System>Help and Support as a starter, cannot find direct references right now, sorry.


Of interest. Speed up boot Post:-
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by mramsey on 2007-09-30
> **amonrath said:**
> my old system has a "initio sata  raid card" which has it's own bios with two sata's hookedup to it, my feisty takes 8 minutes to runup and since i'm not that bright on linux is there a device detect and install utillity as i thought feisty being smaller it would be faster than my microsofts it was abit of a #$%&*#@ to get all the os's to sit beside each other as i've never tried triple boot but i found that Xp 1st then Vista  then linux as vista's bootloader wouldn't pickup ubuntu on my old girl so i've got two bootloaders to go thru but it works sweet ive managed to get beryl to work and found my old girl pushes it along sweet,is their a better g-card for my k7 msi 6450 m-board it's got a ati radeon 9550 agp,yeah i know it's an oldie but i get a kick out of pushing it along harder n harder can anyone help please?:lolflag:

I believe that your RAID card is software Raid as opposed to true hardware raid.  Software RAID will use you system resources to run it. True  Hardware RAID uses its own "OS"(for lack of a better term) and runs itself thus booting faster because it is not using your system.:)

---

