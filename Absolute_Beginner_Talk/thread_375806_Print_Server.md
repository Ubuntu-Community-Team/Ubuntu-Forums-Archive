---
title: "Print Server"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Hamm on 2007-03-04
I have a mixed network. All of my windows boxes print to a printer that is on a printer server device with it's own address. Can I have my Linux boxes do the same? How do I do that?

Hank

---

### Post by HereInOz on 2007-03-04
You have to determine how the printers are shared on the network, and they are probably shared as SMB (Windows) shared printers.  If this is the case, go to System > Administration > Printing and run the printer set up wizard to add the printer as a Windows printer.

Provided the drivers are available, it should be a matter of install the printer and that will do it.  If, however, they are not SMB shares, then you are going to have to find out how they are addressed on the network.

Hope this helps.

---

### Post by Hamm on 2007-03-04
The printer is on a netwok device i.e. 192.168.0.110. It is on 24/7.

---

### Post by Hamm on 2007-03-04
I added the files and it has the correct drivers and wrapper. When I send a test page the job goes in the que but the printer pauses job in a few seconds. I hit resume but it goes to the same thing.

---

### Post by Hamm on 2007-03-25
Still having problems. The printer is not conneceted to any Windows machince. The printer is connected to a print server device, (i.e. 192.168.0.110). All of my window machines can print to it without having any problems. I should be able to print to the same device from any Linux boxes just as easy.......right. The drivers are in the linux boxes, but I just can't get them to print. There must be something simple that I am missing.

Hamm

---

### Post by Hamm on 2007-03-26
> **Hamm said:**
> Still having problems. The printer is not conneceted to any Windows machince. The printer is connected to a print server device, (i.e. 192.168.0.110). All of my window machines can print to it without having any problems. I should be able to print to the same device from any Linux boxes just as easy.......right. The drivers are in the linux boxes, but I just can't get them to print. There must be something simple that I am missing.

Hamm

BUMP any ideas??????:confused:

---

### Post by Patrick K on 2007-03-26
I have my D-Link PS working fine. I used this page to set it up. I don't know if it will work for you. 
[http://gentoo-wiki.com/HOWTO_D-Link_DP-100_HW_Printerserver](http://gentoo-wiki.com/HOWTO_D-Link_DP-100_HW_Printerserver)

---

### Post by Hamm on 2007-03-26
Well with help I did get to work. I added the though CUPS and selected "LPD". 

At the address I entered "lpd://123.456.0.122/queue" then picked the correct printer and driver.

Glad to say that all 6 of my Linux boxes are printing to the server.

Hamm      :KS

---

