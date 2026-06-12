---
title: "HELP! Ubuntu messed up XP partition!!"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by Wesley on 2006-04-06
hi guys

i've been using Ubuntu for around 6 months, dual boot with winXP Professional

decided to give Flight 6 a try

boot up PartitionMagic and deleted Ubuntu partition

boot up winXP CD to fix the MBR by fixmbr

all went fine perfectly, boot up straight to winXP

boot up Ubuntu Flight 6 CD

choosed the empty space (15GB) and created partition automatically, when starting to install the main Ubuntu base, changed to red and a warning saying error partition, cannot find ext3 or something like that. thought never mind, Flight 6 doesnt work well. so i reboot the laptop

got message saying "missing operation system"

thought its bit odd so boot up PartitionMagic, guess what!!! yellow bar with error 114, oh nooooo!!!

but i can boot up SLAX live CD and viewing XP files, but i really need to fix the XP partition but how??

help!

thanks for reading

cheers

---

### Post by frodon on 2006-04-06
It's because the boot sector isn't on your XP partition i think.

So boot on an ubuntu install CD, go to the partition step, then edit your XP partition and add the boot sector (Bootable flag on) on it, save & exit then reboot your computer and it should be good.
[IMG]http://users.bigpond.net.au/hermanzone/p3/i2982op.gif[/IMG]

---

### Post by Wesley on 2006-04-06
boot sector? will fixmbr fix it? fixmbr doesnt work when i tried it, also fixboot too

there's no partition in the whole hard drive, partitionmagic just show it as yellow bar as "error 114". what does it mean?

i think i'll wait till i get home (am at work) then will back up all personal data from XP via SLAX live CD then will try your way

thanks :)

---

### Post by bigken on 2006-04-06
hi you could try booting from winxp disc go to console and type bootconfig /rebuild
if this dont fix  your windows do a repair install hope this helps ;)

---

### Post by Wesley on 2006-04-06
hi

do you think the XP partition is damaged or just the boot sector?

cheers

---

### Post by bigken on 2006-04-06
Hi try fdiskmbr 1st then fixmbr then fixboot exit (in console) if that dont work go to console again and and type bootcfg /rebuild failing that backup all data and try a repair install you said you can read your files so you should have no probs backing them up;)

---

### Post by Wesley on 2006-04-06
fdiskmbr?

the command is not recognized!

---

### Post by Wesley on 2006-04-06
THANK YOU THANK YOU, got it working by booting up Ubuntu CD and turned on the flag, reboot, xp is now working :)

thanks again

---

### Post by frodon on 2006-04-06
Glad it worked :)

I got the same problem at the time with a failed intall on my sister's PC, i beleived she was going to killing me, i'm alive only because i found this tip lol.

---

### Post by bigken on 2006-04-06
[QUOTE=Wesley]fdiskmbr?

the command is not recognized![/QUOTE]

sorry its fdisk mbr 

but your are sorted now so it dont matter pleased you got your prob solved 
;)

---

