---
title: "keyboard design"
date: 2007-04-23
forum: Apple Intel Users
---

### Post by thava on 2007-04-23
Today i am going to install Ubuntu on my MacBook, before  that i have some questions.

Which keyboard design should i choose during the installation (my keyboard is danish design) ?
MacBook Intl
Danish Macintosh

Does the keyborad work on boot (Using Grub) ?

Can I use my external monitor with 1680x1050 resolution?
Can I use my Wireless?
Can I use my Bluetooth?

How can i use right click ?

My MacBooks spec:
    * INTEL CORE 2 DUO 2.0 GHZ
    * 1GB DDR2 SDRAM 667MHZ
    * 80GB SERIAL ATA HD
    * 64MB SHARED INTEL GMA 950 GRAFIK
    * 6X SUPERDRIVE
    * 13,3" GLOSSY WIDESCREEN MONITOR
    * BLUETOOTH, ETHERNET, FIREWIRE
    * WIRELESS NETVÆRK 802.11G
    * BUILD IN WEB CAMERA


Thanks in advance

-- 
Thavarajah Sabanathan

---

### Post by ronocdh on 2007-04-23
I have a MacBook Pro (C2D), but I'll let you know my experience. Keyboard rarely works in GRUB. This is a pain because I am triple booting, and to get into XP I have to hard shutdown about 5-6 times in order to have the keyboard working on the GRUB screen.

I use a USB mouse while installing and setting up, not only for the right click functionality (which isn't set up initially), but also because the trackpad behavior is horrendous. You can install Gsynaptics to fix this, and also edit your mouseemu to tame it. (That has worked wonders for me! Thanks to niklas-komani and Tyrdium for getting it worked out.)

Bluetooth I haven't tested myself but I've heard great things about OBEX, at least in KDE.

Wireless for you should be fairly simple. Do you know which wireless chipset you have? If not, use **lspci** (if it's unknown, try **sudo update-pciids**). I think your MacBooks will be pretty easy to get up, but maybe the C2D MBs are also using the Atheros, which the MBPs have? Someone please teach me this. =)

External monitors take work, but I've seen it done a lot. And with your integrated Intel graphics (*shakes fist*), your setup shouldn't be too terrible.

As for keyboards, not sure. You can always easily change by reconfiguring xserver-xorg, so play around with what suits you best. Good luck!

---

### Post by thava on 2007-04-23
Thank you so much for ur reply.

I only have two important problems:

1) Now I got installed Ubuntu, and I can't get my wireless work. I have try lot of tutorials, but no help.
2) I can't get my external monitor to work. 

any suggestions?

Thanks in advance

Thavarajah Sabanathan

---

