---
title: "I need XP back!"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by sam510 on 2007-09-17
Alright well I really liked ubuntu, but It didnt support the games I played. So ive decided to keep ubuntu but go play my games in vista. I tried booting XP from the grub loader and it just hangs at Starting up.. Now i've tried to go repair it the fixmbr command, but It would just give me an error when It tried to load the windows boot loader. It would say Disk read error press ctrl+alt+del to restart. Ive downloaded and burned over 5 CD boot disks, I can succesfully but back into ubuntu but whenever I try to use the same software to boot into the windows partition it still hangs there. I know for a fact which partition XP is in but it just wont boot on any kind of boot loader, I'm very confused and im 100% sure its not a hardware issue. Before I installed ubuntu XP would boot fine.

---

### Post by rybu on 2007-09-17
Do you have a Windows recovery partition or CDs?  Without knowing anything more about your setup, I'd try to boot from something other than grub.

---

### Post by chicoicho on 2007-09-17
Here link for Boot Loader ,writhe on cd and boot .Link [http://ivkanum.hit.bg/images/bootloader.iso]("http://ivkanum.hit.bg/images/bootloader.iso")

---

### Post by sam510 on 2007-09-17
> **rybu said:**
> Do you have a Windows recovery partition or CDs?  Without knowing anything more about your setup, I'd try to boot from something other than grub.

Ive tried to recover the boot loader from the windows CD but like i said it made it worse. Ive also tried alot of boot cds, None of them would work when it would try to boot xp it just doesnt load it. I dont know why.

---

### Post by debianchick on 2007-09-17
> **sam510 said:**
> Alright well I really liked ubuntu, but It didnt support the games I played. So ive decided to keep ubuntu but go play my games in vista. I tried booting XP from the grub loader and it just hangs at Starting up.. Now i've tried to go repair it the fixmbr command, but It would just give me an error when It tried to load the windows boot loader. It would say Disk read error press ctrl+alt+del to restart. Ive downloaded and burned over 5 CD boot disks, I can succesfully but back into ubuntu but whenever I try to use the same software to boot into the windows partition it still hangs there. I know for a fact which partition XP is in but it just wont boot on any kind of boot loader, I'm very confused and im 100% sure its not a hardware issue. Before I installed ubuntu XP would boot fine.
Try this open up terminal and type this 

sudo update-grub
enter password reboot to see if worked 

if not than get _[Super Grub]("http://supergrub.forjamari.linex.org/")_, burn to CD reboot This is a great disk to have around for emergencies.

---

### Post by uxe1 on 2007-09-17
put in your xp disk and let it start to install
when it gives you the option to press r to repair or to install new continue to install, it will then say ther is another windows iinstalled and installing 2 is not recremended. then it gives you the option to repair again, choose repair now, it wil take about as long as a fresh install would. finaly after it is all done (and youve registerd with loard Gates again) you will have to reinstall grub. im sure there are better ways that ppl who have a good understanding of computers use. but this will work for sure, and you wont lose any thing from either your old windows install or your ubuntu. ive had to do this a coupla of times cause i screwed around with my windowz files after installing ntfs-3g. and to tell the truth ill prolly have to do it again. so if you find an easer way post it here so i can know ok?

---

### Post by Crafty Kisses on 2007-09-17
> **debianchick said:**
> Try this open up terminal and type this 

sudo update-grub
enter password reboot to see if worked 

if not than get _[Super Grub]("http://supergrub.forjamari.linex.org/")_, burn to CD reboot This is a great disk to have around for emergencies.
Yeah, that should work, and Super-GRUB is really great too.

---

