---
title: "settings for Efax, Conexant HCF V90 modem"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by zebzeb on 2006-12-22
I installed a driver for my moden, Gnome-PPP autodetected it and can use it perfectly.
Detected it at dev\ttySHCF0 
Init 2 ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 (don't know what any of this means)
I don't need to use it for the Internet as I have broadband but would like to use it for fax.

I have tried Efax, initially (dev\)modem but after I got gnome-ppp to auto detect it I changed location to ttySHCF0. It always reports an error

efax-0.9a: 44:36 Error: can't determine fax modem class support
if I manually enter class (I've tried them all)
efax-0.9a: 45:40 finished - invalid modem response

Have tried different things for capabilities, the defaults, also googled it and tried 0,1,1.0,8,80 but efax said not enough arguments or something similar.

anyone have an idea? Or another way to fax of print-to-fax????

PS. more info about my modem: 00:09.0 Communication controller: Conexant HCF V90 56k Data/Fax/Voice/Spkp PCI Modem (rev 08)

PPS baby is teething and I only started linux last week + baking for Christmas so go easy if I'm being silly?

---

### Post by zebzeb on 2006-12-23
Ignor my sillyness, I think its the restricted driver I downloaded, it prevents fax use, I should have read all the instructions before posting!

---

