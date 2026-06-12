---
title: "2 HDs. One with XP and installing Ubuntu to another"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by nisukka on 2005-08-07
Hi!
I have 2 hard drives in my computer. I have Windows XP installed on the other and would like to install Ubuntu on to the other one. Is there anything special I need to do during the installing of Ubuntu or does it automatically set up my computer so that when I turn it on, I can choose to load either Windows or Ubuntu?

I don't want to install them on to same hard drive but separate ones. Any guides for situations like this?

Thanks!

---

### Post by roland on 2005-08-07
[QUOTE=nisukka]Hi!
I have 2 hard drives in my computer. I have Windows XP installed on the other and would like to install Ubuntu on to the other one. Is there anything special I need to do during the installing of Ubuntu or does it automatically set up my computer so that when I turn it on, I can choose to load either Windows or Ubuntu?

I don't want to install them on to same hard drive but separate ones. Any guides for situations like this?

Thanks![/QUOTE]

When installing Ubuntu it asks where you want your Ubuntu installation. Choose wisely, the Ubuntu installer explains a lot about it while installing. After choosing where to install, Ubuntu asks to create a config file for booting the computer with GRUB. GRUB is a so called "boot loader" and creates a boot menu when starting the computer, so you can choose to start either Windows or Ubuntu.

Maybe this will get you a little further, if you have any questions on this, or on accessing your Windows drive from Linux and vice versa, don't hesitate to ask.

Roland.

---

### Post by Rapaport on 2005-08-07
Be cautious when you do this. If for some reason the GRUB bootloader gets ruined, corrupted, bombed, etc. you're going to need your Windows install CD or your Windows partition is lost. Make sure you have that CD before you try to install Ubuntu. 

If your bootloader gets messed up, pop in your Windows installer CD. Hit "R" to run the rescue console and once you get your C:\ prompt type "fixmbr" w/o quotes.

---

### Post by heart_reaver on 2005-08-07
heeya 

you can install grub boot loader after installing ubuntu. For more help go to 

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

---

### Post by roland on 2005-08-07
[QUOTE=Rapaport]Be cautious when you do this. If for some reason the GRUB bootloader gets ruined, corrupted, bombed, etc. you're going to need your Windows install CD or your Windows partition is lost. Make sure you have that CD before you try to install Ubuntu.

If your bootloader gets messed up, pop in your Windows installer CD. Hit "R" to run the rescue console and once you get your C:\ prompt type "fixmbr" w/o quotes.[/QUOTE]

If the MBR has been corrupted or otherwise erased, the BIOS can't find a proper boot partition, so it is not true that your Windows partition gets really "lost". It only becomes "invisible" for the current Windows installation. Rapaport is right on the way to solve this. The only thing the Windows-cd does, is rewriting the MBR, so Windows recognizes its own partition again. The other alternative is to reinstall GRUB, I have explained how to do that in [this](http://ubuntuforums.org/showpost.php?p=290441&postcount=2) topic.

It's up to you to decide to install GRUB immediately, or first use the recovery-cd, so you got a good feeling that *something* is starting.

---

