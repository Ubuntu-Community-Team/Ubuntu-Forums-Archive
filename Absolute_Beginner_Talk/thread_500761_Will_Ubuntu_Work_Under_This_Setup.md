---
title: "Will Ubuntu Work Under This Setup?"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by shamushand on 2007-07-14
I've been thinking for a while about putting Ubuntu on my main machine, but I don't know the best way to do it. A triple-boot with Vista, XP and Ubuntu seems to be the way to go, but might be complicated to set up. Here are my full system specifications:

2.53Ghz Intel Celeron D
1,277MB RAM
256MB nVidia GeForce FX 5200

Current Hard Drive setup:

HD 1: Vista (80GB)
HD 2: XP (80GB)

Setup I want:

HD1: Vista (80GB)
HD 2: XP (40GB) + Ubuntu (40GB)

Here's how I would like my MBR to be:

(Windows Bootloader)

Windows Vista (Loads Vista)
Windows XP (Loads XP)
Ubuntu Linux (Loads GRUB)

But I hear GRUB has to be out on top? :confused:

Internet:

Netopia 3D Reach Wireless card, model TER/GUSB-N
128-Bit WPA Network Encryption

How would this work with NDiswrapper? 

Could I get this to work? :confused:

---

### Post by poltiser on 2007-07-14
I have 1 Sata and 2 IDE HD. Sata divided into 4 partition 40 MB Windows XP (ntfs) + 18 eet3 + 18 et3 + .5 MB swap
1 IDE in 3 partitions: ntfs with temporary and data files of windows programs and system + et3 with Ubuntu 7.04 AMD64+ et3
2 IDE with collection of documents, music, pictures and so on...

It works well...

Regards.

---

### Post by viciouslime on 2007-07-14
All that will work fine. Grub doesn't HAVE to be on top, it just will be by default, it's a little more tricky to do it how you want because the windows bootloader won't automatically detect ubuntu.

Why would you really want the windows one first though? Why not just use grub and have Vista, XP and Ubuntu all appear on the same menu? Grub is an awful lot more powerful and generally better all round, plus this way will be the default after ubuntu has installed anyway, so it requires no configuration (unless you want to change the default OS)

EDIT: Not sure about your wireless card though, try it using the live cd, you can install ndiswrapper there just as you normally would :)

---

### Post by MockY on 2007-07-14
Why not install only Ubuntu and run any other OS with VMware-server or Virtualbox?

---

### Post by shamushand on 2007-07-14
> **MockY said:**
> Why not install only Ubuntu and run any other OS with VMware-server or Virtualbox?

Because my parents will be very, very mad :lolflag:

Either way, is there a guide somewhere of how I can set this up? :)

---

### Post by zach12 on 2007-07-14
hmm could you get rid of xp 
if not try googleing 3 way boot
have fun

---

### Post by Dennis the Menace on 2007-07-14
I spotted this guide the other day, triple booting XP,Ubuntu & Pclinux.
don't know if it's any good to your poser, heres the link nothing to lose by looking.
[http://www.mediafire.com/?eddbggc2vjn](http://www.mediafire.com/?eddbggc2vjn)
:)

---

