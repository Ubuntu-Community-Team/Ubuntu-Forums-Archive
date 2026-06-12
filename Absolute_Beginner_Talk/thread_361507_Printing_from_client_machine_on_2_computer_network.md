---
title: "Printing from client machine on 2 computer network"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Jamface on 2007-02-14
I have Ubuntu 6.10 dual boot installed on my desktop and linked by ethernet via ADSL modem router to by XP only laptop.  The printer (HP OfficeJet G85) is USB connected to the PC. I can print from the PC, after installing HPLIP.ppd,  but not from the laptop.  Ubuntu seems to recognise the existence of the laptop, i.e. the name of the network as set on the laptop appears in the network window on the Ubuntu PC.   Please could someone suggest where the problem is likely to be? Do I need to grapple with CUPS on the PC? Apart from setting up the network to give me internet access I haven't tried to establish a specific network link from PC to laptop.
Bill

---

### Post by mssever on 2007-02-14
I'm not quite sure if I understand your configuration. Are you having trouble printing from an XP machine to a printer attached to an Ubuntu machine? In that case, you need to either configure Samba to share your printer, or publish it using CUPS ([http://localhost:631)](http://localhost:631)). I don't remember if there's a graphical way to accomplish this. Then, add the printer in XP. If you used CUPS, you'll need to tell XP that it's a UNIX printer and provide the URL (ipp://ip.address.of.ubuntu.box/printers/printer-name)

---

### Post by Jamface on 2007-02-15
Many thanks, mssever. :)  I'll try CUPS and see how I get on.
Bill

---

