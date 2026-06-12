---
title: "Connecting to printer through Netgear print server"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by phil.munck on 2008-03-01
My physical setup consists of Linksys wireless DSL modem/router into which are plugged two Windows XP machines and this system with Gutsy Gibbon and a Netgear WGPS606 wireless print server with the wireless feature disabled (I am only using it as a print server).  All the units are connected with Ethernet cables.  The IP address of the printer router is 192.168.1.202 and the printer is connected by USB into LPT1 of the printer server.  Interrogating printer server by browser through its IP address, the printer's name is "photosmart 7900 series" (it is, in fact, a PhotoSmart 7960).
The Windows computers find a printer name of "hp photosmart 7900 series" and a port name of "IP_192.168.1.202P1".  In setting up the printer in Windows, I identified the printer as a local printer.
I have been working in Ubuntu with system-config-printer.py 0.7.75 and have tried every permutation of new printer settings I could think of but still am unable to get a test page printed.
I'm sure that something simple is eluding me but I can't figure out what.
Any help is appreciated.

---

### Post by dcstar on 2008-03-01
> **phil.munck said:**
> My physical setup consists of Linksys wireless DSL modem/router into which are plugged two Windows XP machines and this system with Gutsy Gibbon and a Netgear WGPS606 wireless print server with the wireless feature disabled (I am only using it as a print server).  All the units are connected with Ethernet cables.  The IP address of the printer router is 192.168.1.202 and the printer is connected by USB into LPT1 of the printer server.  Interrogating printer server by browser through its IP address, the printer's name is "photosmart 7900 series" (it is, in fact, a PhotoSmart 7960).
The Windows computers find a printer name of "hp photosmart 7900 series" and a port name of "IP_192.168.1.202P1".  In setting up the printer in Windows, I identified the printer as a local printer.
I have been working in Ubuntu with system-config-printer.py 0.7.75 and have tried every permutation of new printer settings I could think of but still am unable to get a test page printed.
I'm sure that something simple is eluding me but I can't figure out what.
Any help is appreciated.

I have Samba running on my 7.10 with a local USB printer, and I can connect to it with the standard System-Administration-Printing (gnome-cups-manager) and selecting the Windows network printer options.

---

### Post by phil.munck on 2008-03-07
Thanks for the input but in this case the printer is not connected to a Windows computer.  It is plugged into the wireless router through a print server device.  I installed Samba but I still can't detect either the print server or the printer.

---

