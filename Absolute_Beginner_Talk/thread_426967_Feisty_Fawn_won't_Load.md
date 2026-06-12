---
title: "Feisty Fawn won't Load"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by DrtBikDave on 2007-04-29
I am relatively new at this and tried to upgrade from Edgy to Feisty. After it went through the process and said it wanted to reboot It seemed to lock up at boot up. Furthermore I used to have four choices to choose from after bios post ( Linux kernel..., Linux safe mode.., Memory test, and windows XP) now I have eight.the first four are duplicates of the new version of Linux, then the old version of Linux, still have the memory test and windows XP. Right now I am using XP.



If it helps here is my computer specs


Asus P5WD2-Premium Mobo
Intel 640 3.2 ghz Processor
1 Gig of Corsair PC5400 ddr2
Pny 6800 PCI express video card
Maxtor Sata II hard drives
Ultra 650w Pwr supply

I think that is all the pertinent hardware.

---

### Post by mikeyphi on 2007-04-29
You GRUB menu is correct.....Try booting into the old system - Dapper...if that works - and it should - then your upgrade has gone wrong.

---

### Post by DrtBikDave on 2007-04-30
Thanks for the help, I was able to get into the older version. Now how should I go about upgrading to Feisty Fawn (or should I leave it alone) and get rid of those other choices?

---

### Post by mikeyphi on 2007-04-30
> **DrtBikDave said:**
> Thanks for the help, I was able to get into the older version. Now how should I go about upgrading to Feisty Fawn (or should I leave it alone) and get rid of those other choices?

The official guide: [http://www.ubuntulinux.org/getubuntu/upgrading](http://www.ubuntulinux.org/getubuntu/upgrading)

Hope it works!!

---

### Post by Pobega on 2007-04-30
Just so you know, whenever there is an updated kernel uploaded to the repositories it is almost automatically added to the menu.lst, so you'll see it there next time you boot up.

---

### Post by DrtBikDave on 2007-04-30
Thank you very much Mikeyphi, Youve been a great help. 

  Pobega, I also appreciate your assistance. That was how I found out about the upgrade aand I tried by using the link and the download failed. So I tried it again and that is when I couldn't boot into Ubuntu it just froze up. After Mikeyphi suggested to try my old version which worked. Now I want to know how to get the 2 sets of boot options that don't work for Feisty fawn or will fiesty do it for me when it does load correctly?

---

