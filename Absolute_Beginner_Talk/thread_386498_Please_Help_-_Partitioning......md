---
title: "Please Help - Partitioning....."
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by SurR3AL on 2007-03-17
hey....well the only OS on my comp right now is ubuntu 6.10. but i've decided to also install XP coz i wanna play some games n stuff that dont work properly on ubuntu. but by no means do i wanna remove ubuntu tho. it'll still be my primary os. anyway, i don't have an XP cd, but i have a hp comp, so there is an inbuilt recovery partition that i can invoke from the BIOS boot time screen and i can reinstall XP. now, i dont wanna lose my data n configs of ubuntu. so is there any way i can install XP on a new partition without wiping ubuntu and then reinstalling it? my partition scheme as of now is given below:

HDD -> 80GB WDC

"/" -> hdc2 -> 20GB
"/home" -> hdc3 -> 47GB
hdc1 -> 5GB     <- (this is the recovery partition)

any help would be welcomed. thank you so much. :)

---

### Post by mikewhatever on 2007-03-17
The question is whether the recovery partition installer is smart enough to ask for the partition to install to. Have you even tried to launch it to make sure it woks?

---

### Post by SurR3AL on 2007-03-17
no i've never done it, but suppose it does ask me, i just make another partition with gparted and install XP on it? is that all?

---

### Post by mikewhatever on 2007-03-17
> **SurR3AL said:**
> no i've never done it, but suppose it does ask me, i just make another partition with gparted and install XP on it? is that all?

Well, sort of. Installing Windows after Ubuntu overwrites the MBR, so you'll need to reinstall GRUB from Ubuntu live cd and edit GRUB menu.lst to boot Windows.

---

### Post by SurR3AL on 2007-03-18
i really dont wanna mess around with bootloaders....so guess i'll wipe ubuntu then install XP then ubuntu again....but i have one more question. I'll now install XP and linux on my 80 gig hard drive. i'm soon gettin a 320GB internal hard drive. can i just partition it as ext3 n use it? winXP will detect is as drive F: or whatever, but what about ubuntu? should i like use gparted to make it "/home" or will ubuntu detect it n make a new entry in /media? coz i just want to use that 320gig hdd as storage for all my movies n stuff....

---

### Post by mikewhatever on 2007-03-18
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by SurR3AL on 2007-03-18
ooh that makes it crystal clear :D
@mike - Thank you SOOOO much! :)

---

