---
title: "Vista has dissapeared after Ubuntu Ultimate Gamer Edition installation."
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by mr_finn on 2007-10-16
I had Vista installed on one 80 gb (C) drive and then installed Ubuntu on another 160 gb (D) drive with everything working fine and dual booting from the grub menu.

It was not long before my Vista drive was filling up as I/we play alot of large games here, so I decided it would be better if I had Vista on the larger hardrive to accomodate all this software.

I installed Vista first on the 160 gb drive and updated it, installed all my apps and games etc and now  have installed Ubuntu on the 80 gb drive. 

On the first reboot after Ubuntu installed I was expecting the grub boot menu screen but it just continued booting into Ubuntu, Vista seems to have gone.

I can see all the Vista files still on the drive while using Ubuntu but I cant boot Vista at all.

Any ideas?

---

### Post by hyper_ch on 2007-10-16
You could try adding vista manually to your menu.lst

---

### Post by pancakelizard on 2007-10-16
**fdisk /mbr** maybe?

---

### Post by LowSky on 2007-10-16
You could open up your box and disconnect the ubuntu drive and make sure Vista will still boot
or change which hard drive to boot from in bios until you fix Grub

---

