---
title: "How to Connect to Internet Question"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by rmaier on 2006-03-14
New computer, loaded with Linux-Ubunto. Familiar with Windows apps, but lost in Ubunto. Trying to setup  connection  to internet using Cox High Speed Internet Cable. Originally connected cable and modem, loaded their CD, the CD displayed the files on the CD, but did not load. Cox staff advise me to turn Computer off, connect cables to computer and cable modem. Cable modem plug into power outlet,and turn computer on.  They tell me no software needed installed, the internet connection will automatically configure.  So, if true, where do I go to connect to Internet, and will it automatically configure using Cox as the server?  If this didn't work they told me to check my TCP/IP address? Where do I go to find this in Ubonto? Appreciate help... Thanks...

---

### Post by TrendyDark on 2006-03-14
Ubuntu* not ubunto. . lol

Anyways, first, see if Ubuntu is detecting your network interface card.

Goto System> Administration> Networking and see if your card is listed there. If so, configure it from this screen. Select DHCP, somewhere (i'd say where but i'm on my windows pc). 

If it still will not work then, see if you have a reset button on your cable modem. I remember I couldn't get mine working because I didn't reset the modem. . took me 3 days to figure that out.

---

### Post by rmaier on 2006-03-14
your right, Ubuntu...lol...thanks for the reply, will try your suggestion. thought i had to have the software loaded before internet service started, cox internet scheduled to be turned on tommorow, will wait to see. Am also on my windows pc. thanks....

---

### Post by skymt on 2006-03-14
[QUOTE=TrendyDark]Select DHCP, somewhere (i'd say where but i'm on my windows pc).[/QUOTE]

System > Administration > Networking > Network Connection > Properties > Configuration. Although that shouldn't be necessary, DHCP is the default. Cable modems should Just Work.

---

### Post by mips on 2006-03-15
[http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)

Follow the above first and if you get stuck tell us where.

---

