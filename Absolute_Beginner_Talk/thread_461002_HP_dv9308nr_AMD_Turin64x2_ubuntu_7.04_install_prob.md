---
title: "HP dv9308nr AMD Turin64x2 ubuntu 7.04 install problems"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by paularglinux on 2007-06-01
Dear All:

I'm using ubuntu on several PCs, Recently I bought a HP dv9308nr notebook with AMD Turion62x2 , nvidia 6150, 2 GB RAM & SATA disk 120 GB.

I tried to install ubuntu  and failed, until i tried with boot noapic & noirqdebug options, then the liveCD run ok, and the hardware recognition works fine, i was able to do the normal install on the HDD, (FULL instalation, i'm not interested on runing windows at all), but after rebooting without the CD the startup process hangup during the splash windows with the bar nea by  the middle.

Can anyone help me with a "How to install procedure" ?? for this machine or give me some other tips , I don't want to reinstall the Sabayon 64 version for AMD, that i installed first and worked fine. I prefer ubuntu to have the same OS like the rest of the PCs at home. (My wife & I , both use ubuntu , there are no winblows machines at home)

---

### Post by blazercist on 2007-06-01
why dont you edit the boot line in grub and add those two options, when the grub menu comes up select your kernel and hit e and then add those options to the boot line, once you're in and you reach a desktop you can : sudo gedit /etc/boot/menu.lst and add those options permanently.

---

### Post by psharboneaux on 2007-10-02
Actually, adding the following entries work the best with the HP dv9308nr laptop;

vga=791 pnpbios=off irqpoll nomsi nomce

By using these settings, Ubuntu runs very smoothly on this laptop.  Also, if you follow the settings on this [link]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/"), the suspend and hibernate features work like a charm.

---

