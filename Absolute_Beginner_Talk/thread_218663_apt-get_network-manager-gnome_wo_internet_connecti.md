---
title: "apt-get network-manager-gnome w/o internet connection?"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by palejade on 2006-07-18
I notice that a lot of the instructions for setting up a wireless connection start with something like "apt-get install network-manager-gnome".. and then Ubuntu tries to download it, but if I don't have a connection already in Linux, how am I supposed to get the necessary files?

](*,) 

I believe I have U 6.06. And I do have wireless connection on this computer as it is dual booted with XP, so downloading something and then just going into Linux and opening it up isn't necessarily an issue. 

In Network Manager it shows the modem and ethernet card (eth0), but not the wireless card. 

Wireless card is Netgear WG311 - I checked the list and it's a supported driver. :)  

Help?

---

### Post by Skia_42 on 2006-07-18
You need internet to use the apt-get command. You can plug your computer into an ethernet outlet using a cord and download the apps/ use the internet untill you get wireless working.

---

### Post by palejade on 2006-07-18
Well, i'd have to move my computer all the way across the house and into the kitchen, and that's not really a viable option. Is there another location that I can download the necessary files from?

---

### Post by skale on 2006-07-18
Use a different computer to download the files straight off the internet and transfer it to your computer. If you can find a .deb package, great install it with **sudo dpkg -i nameofpackage.deb**

If you cannot get .deb, download the source code (in either .tar.gz or .tar.bz2) and build it, with this:[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by palejade on 2006-07-20
ok. i'll see what i can do. 

thanks.

---

