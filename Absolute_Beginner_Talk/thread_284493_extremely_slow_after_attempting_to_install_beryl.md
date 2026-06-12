---
title: "extremely slow after attempting to install beryl"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by aznboi on 2006-10-25
i tried to install beryl, didnt really work, but after i followed this guide:
[http://www.wikitut.org/index.php?title=How_to_Install_ATI_Graphics_Card_Drivers_under_Linux](http://www.wikitut.org/index.php?title=How_to_Install_ATI_Graphics_Card_Drivers_under_Linux)
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```
and i rebooted, my comp is reallyyyy slow now... any ideas? thnx

---

### Post by barkej on 2006-10-25
It sounds like you need 3d enabled drivers for your graphics card.  What kind of card do you have?

---

### Post by aznboi on 2006-10-25
thnx for the reply! this is my video card:

Diamond Stealth S85 -ATI Radeon 9250

[http://www.diamondmm.com/S85AGP.php](http://www.diamondmm.com/S85AGP.php)

---

### Post by Redache on 2006-10-25
[Automatix]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38")
If you're unfamiliar with installing drivers, use Automatix to install the drivers you need. I think they're the legacy drivers?

---

### Post by aznboi on 2006-10-25
just installed automatix, it doenst have hte legacy driver u reccomended... thnx anyways!

any other ideas? thnx!

---

### Post by aznboi on 2006-10-26
*bump* any help please?:-D

---

