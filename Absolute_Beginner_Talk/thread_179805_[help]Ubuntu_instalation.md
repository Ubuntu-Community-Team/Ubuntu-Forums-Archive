---
title: "[help]Ubuntu instalation"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by NaNoSoLdIeR on 2006-05-20
hy i'm a big newbie to linux and i need to install it, i have downloaded the ubuntu instalion for i386 and the live version for the same i386, then burned it to a cd using nero, 

using either the live or the install gives me a warning about ethernet hardware
"No ethernet card was detected, but a Firewire interface is present", i have an linksys 190 10/100 Fast ethernet controller as my ethernet board I have checked this on windows,
and then it asks me if i intend to use firewire ethernet...

my next problem is configuring the internet...i really don't know how to do this one... my net hardware is as follows, i've got a cable modem (that hasn't got dial-up) from there the internet cable goes to my router and then to my pc. the router part in windows doesn't affect anything i don't know if it will affect ubuntu

next up I have a sata harddrive from maxtor that isnt showing either in the partition part of the install or in after instalation... don't know i will had this one

can someone help me on these 3 questions or point me to newbie tutorials that explain those three points in detail...

---

### Post by cleverselfreferentialname on 2006-05-20
Sorry, could you elaborate on your ethernet card? Googling doesn't turn up any hits for "linksys 190".

---

### Post by NaNoSoLdIeR on 2006-05-20
[QUOTE=cleverselfreferentialname]Sorry, could you elaborate on your ethernet card? Googling doesn't turn up any hits for "linksys 190".[/QUOTE]
Linksys
	

Fast Ethernet 10/100 PC Card
	

Axis AX88190
	

Yes
	

No
	

NIC is found, and cardctl commands show it present, haven't gotten it to be recognized that it's a NIC.
	

18 June 2005 : 0941  found this at this page [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards)

---

### Post by cleverselfreferentialname on 2006-05-20
Theres the axnet_cs driver, but it might only be for PCMCIA cards based on this chipset. Is this a PCMCIA card?

---

### Post by Sef on 2006-05-20
Are you using a laptop or a desktop?

---

### Post by NaNoSoLdIeR on 2006-05-20
[QUOTE=cleverselfreferentialname]Theres the axnet_cs driver, but it might only be for PCMCIA cards based on this chipset. Is this a PCMCIA card?[/QUOTE]
nope it's a PCI card

---

### Post by NaNoSoLdIeR on 2006-05-20
[QUOTE=Sef]Are you using a laptop or a desktop?[/QUOTE]
desktop pc i've also noticed i didn't say which version of the ubuntu i'm using, it's 5.10

---

### Post by water8 on 2007-10-19
I have similar problem using 6.06 server on Asus M2A-VM. The error message is "No ethernet card was detected, but a FireWire Interface is present." 

My work around is to use 7.10. And it works!

---

