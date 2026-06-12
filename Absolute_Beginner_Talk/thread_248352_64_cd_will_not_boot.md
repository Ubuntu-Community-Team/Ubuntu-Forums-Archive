---
title: "64 cd will not boot?"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by takiniteasy on 2006-09-01
I have an AMD 64x2 4200+. This will be my first ubuntu box. I can not seem to get the cd to boot, but if I am in windows it will auto play just fine? is there something I am missing to get the iso image working right? This is also my first 64 system and it has a 400 gig hdd sata. Will ubuntu work on this type of system with a duel boot windows/ubuntu. But first I need to know if there are any problems with the iso images or maybe I forgot how to make an iso the will boot lol.

---

### Post by natrixgli on 2006-09-01
hey,

Stupid question, but is your BIOS configured to boot from CD? If not, you might be able to hit a key on boot to select a 'temporary boot device'...


My experience running the 64bit version on an X2 has not been good. The stability on multi-core AMD systems is much better with the 32-bit version. The consensus among most X2 users has been the neglegable gains in performance aren't worth the issues.

After you install, enable the universe repositories and install the K7 kernel, and you'll be all good. 

I'm running a 32-bit version of Ubuntu with kernel 2.6.15-26-K7 on an AMD X2 3800+ with no major issues. I have 2x SATA 120gb drives in software RAID1, and after some minor issues, it's all sussed. 

I suggest you install from the Ubuntu-Server image, and then install ubuntu-desktop on top of it. The server version is going to be a much quicker and lighter install which will increase your chances of getting a bootable system so you can read the logs.

-n8

---

### Post by L_o_N_e_R on 2006-09-01
takiniteasy  plz do not make 2 threads

ya edit your bios so the cd boots before the hd

---

### Post by takiniteasy on 2006-09-01
Sorry for the double thread:redface: thanks for the help I am going to download the 32bit version and see if that works. I have been reading and it seems that the 64 bit has very little support form any disto and I dont really have that much need for a 64bit system, when it comes to linux anyways.

---

### Post by TFX360 on 2006-09-01
> **takiniteasy said:**
> Sorry for the double thread:redface: thanks for the help I am going to download the 32bit version and see if that works. I have been reading and it seems that the 64 bit has very little support form any disto and I dont really have that much need for a 64bit system, when it comes to linux anyways.

It's probably your graphical card. ATI? I can't boot the 64-bit CD too. If your into linux you can edit /etc/X11/xorg.conf after the live cd boots and you get the bourne again shell (BASH). And change the driver to vesa.

---

