---
title: "No GUI when i EFI boot 13.10 live dvd"
date: 2013-12-04
forum: Apple Hardware Users
---

### Post by ResQue on 2013-12-04
When i EFI boot from the ubuntu 13.10 live dvd i get no GUI

I have a 64bit MacBookPro3,1 SantaRosa (late 2008), Intel Core2 Duo, nvidia 8600M GT GPU, and 4gb of ram, EFI 1.1 (64bit, UGA graphics)

I have read the ubuntu community support links on UEFI, and GRUB as well as a lot of info on the arch linux wiki that helped

If i add the kernal param nomodeset i can get to TTY1, i used that to copy the whole /var/log dir

I could really do with some help on where to go next and what support documents i should be reading


xorg.0.log: [http://paste.ubuntu.com/6522651/](http://paste.ubuntu.com/6522651/)

---

### Post by sostacked on 2013-12-07
I have the exact same machine and I got as far as you did. nomodeset allowed the installation in GRAPHICAL MODE (it looked beautifully in 1920x1200!) but upon rebooting, no dice. tried installing nvidia-current, messed around with xorg.conf but got nowhere. Looked around the net and found no confirmed installations on this particular model. If you happen to find something, please post here.

---

### Post by sostacked on 2013-12-07
Managed to get the graphics going with the fbdev driver, just copy xorg.conf.failsafe to xorg.conf and change the driver to "fbdev". Resolution is fine, colors as well. Performance is abysmal. After tweaking ccsm and disabling all eye candy, it is somewhat usable.

After that tried nvidia-173, I get the nvidia logo and then black screen, no backlight, no nothing.

---

