---
title: "[SOLVED] Printer -Access Denied"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by kenboyles72 on 2007-12-05
Ubuntu version - Ubuntu 7.04 - the Feisty Fawn
Network setup - 1 pc w/ubuntu, 4 pc's w/win xp

I finally got my network setup and now sharing files and seeing other pc's on my network. I have installed my printer (epson photo stylus r200) and have it shared, sort of. I can see and install the linux printer in xp, but get access denied. Any suggestions?

---

### Post by mikeyphi on 2007-12-06
Check you've 'shared' the linux printer - under System/Administration/Printing

---

### Post by kenboyles72 on 2007-12-08
well i finally got my printer shared and got the shared printer installed in XP. but when i try to print to it, it fails to print. when i installed it in XP, it said that the server didn't have the correct drivers, so i used the setup cd for the drivers. since the setup cd had only the driver for windoze pc's, should it still be able to print to the linux printer or not?

---

### Post by kenboyles72 on 2007-12-10
Finally got it figured out. I had my printer shared with cups and was also shared through samba. In the samba config, the print caps was set to cups. In Xp, I was setting up the printer through the samba share which was showing up in network places, which was causing errors. I read up on many docs on sharing through cups, so then I tried connecting through http. So I entered the ip addy of the printer, ie -http://xxx.xxx.x.xxx:631/printers/epson_r200. Which was still wrong, because epson_r200 was the share name that I set through samba. So the next time I opened the cups console, I noticed the name of the printer, which was Epson-Stylus-R200. So then I typed - [http://xxx.xxx.x.xxx:631/printers/Epson-Stylus-R200](http://xxx.xxx.x.xxx:631/printers/Epson-Stylus-R200) and was able to print. So, if any other new users are having problems sharing printers, take note of the way you setup your shared printer and the share name :lolflag:

---

### Post by davenport651 on 2008-03-18
How can I tell which way my printer is shared?  I clicked System|Administration|Printing, then checked the boxes to "Share Publish Printers".  Does this mean that my printer is shared through CUPS?  As far as I can tell, the Samba GUI (System|Administration|Shared Folders) in Ubuntu has no means to share printers, only folders.

---

