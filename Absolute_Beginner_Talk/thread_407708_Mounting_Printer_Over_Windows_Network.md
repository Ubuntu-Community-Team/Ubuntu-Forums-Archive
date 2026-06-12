---
title: "Mounting Printer Over Windows Network"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by say592 on 2007-04-12
Ok, so I set up a windows network using a guide I found on here. (the network existed, I guess I just mounted it on my ubuntu machine)

Anyways, I added a printer to my network, connected to my XP machine. The ubuntu uses a wLan card to connect to the network, and all the other computers use LAN cards.

The printer works fine, and I can browse documents on the windows machine via the ubuntu machine, but I can not get it to detect the printer on the windows machine!

I couldnt find a guide on this, but if there is one, just point me to it. Any help is appreciated.

---

### Post by dstew on 2007-04-12
You need to use Samba to access the shared printer, just like you use it to browse windows shares. When  you set up the printer in your Linux system, give it the name

smb://*servername*/*printername*

The *servername* is the name of your Windows computer, and the *printername* is the name you give the printer on Windows when you set it up to share. Your print manager on Linux should find it on the Windows network, then you can install the driver and use it.

---

