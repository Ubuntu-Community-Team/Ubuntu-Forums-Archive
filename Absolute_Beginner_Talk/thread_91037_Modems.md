---
title: "Modems"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by johnmd on 2005-11-16
I'm just getting ready to install Ubuntu 4.5 and have two modems to pick from.
One is a USR 33.6 hardware modem and the other is a ESS-ES56H-PI software modem.
My question is which would be the best choice?
Where I live there is no high speed of any kind available and our EL cheapo phone company only runs 33.6 modems so is the USR the best way to go?

John

---

### Post by Dragonbite on 2005-11-16
With the USR, you don't have to worry so much about trying to get the drivers.  I have been using external USR modems for a while without major issues (I too do not have broadband in the area but at least I can use a 56k modem).

There is a scanmodem utility somewhere I ran across that looks at your modem and tells you what dirvers you need.  Unfortunately this only worked with the 2.4 kernel and said it didn't work with the 2.6 even though it was successful on that same machine with another (older) distribution.

Good luck!

---

### Post by Oceola on 2005-11-16
I've got a USR 5610B internal Serial Modem (actually both serial and software). It configured automatically with what came with Hoary Hedgehog and the US Robotics site has an .rpm package. For my modem, the Rpm driver package doesn't support multi-ports where the Ubuntu drivers do. I spoke to the tech support folks to see if there was a .deb package and they didn't know, that was a couple of months ago.
Check Linmodems,org and search around for Linux compatible modems. There's a lot of info out their which may help with your modem.:) 

You might have to do a little searching to see which /dev/ttyS(?)you wound up on.
You may be better off with the hardware modem.

---

### Post by johnmd on 2005-11-16
[QUOTE=Oceola]I've got a USR 5610B internal Serial Modem (actually both serial and software). It configured automatically with what came with Hoary Hedgehog and the US Robotics site has an .rpm package. For my modem, the Rpm driver package doesn't support multi-ports where the Ubuntu drivers do. I spoke to the tech support folks to see if there was a .deb package and they didn't know, that was a couple of months ago.
Check Linmodems,org and search around for Linux compatible modems. There's a lot of info out their which may help with your modem.:) 

You might have to do a little searching to see which /dev/ttyS(?)you wound up on.
You may be better off with the hardware modem.[/QUOTE]

I just found another modem.
This one is a 3 COM (USR) 56K PCI modem.
I think it a hardware modem but 'm not 100 % sure.
Don't even know where it came from. It works fine in windows:mad: 
Any ideas on this one?
I'll have a look at that Linus modem site too.


 John

---

### Post by nkobel003 on 2005-11-16
Hey, I was wondering if someone could supply a full list of compatible modems for ubuntu--or at least a general list.
Thank you,
Nick

---

### Post by Oceola on 2005-11-17
[QUOTE=johnmd]I just found another modem.
This one is a 3 COM (USR) 56K PCI modem.
I think it a hardware modem but 'm not 100 % sure.
Don't even know where it came from. It works fine in windows:mad: 
Any ideas on this one?
I'll have a look at that Linus modem site too.
 John[/QUOTE]

Most "serial"  (hardware) modems will work for Linux distributions, or so I've been led to believe. Mine is both a serial and PCI modem and was reasonably pricey. I had to replace the PCI modem which was in the system in order to use Linux with this one as the other modem was not supported or no drivers were available. There are some PCI modem drivers available but you may have to search a little. The PCI modems are mostly what they call software or Winmodems. If you have a USR modem and want to know if it's serial capable and you don't have the box or printed material which came with it, if you have a model number this site can help with some drivers and some technical information. It's also through here you can get the .rpm for the 5610b, careful on USR model numbers as some are similar with only a last letter added or omitted.

[http://www.usr.com/support/s-main-menu.asp](http://www.usr.com/support/s-main-menu.asp)

---

### Post by digitalgecko on 2005-11-17
If you have an Office Depot where you live. They sell a great external modem that configures automatically with Hoary and Breezy. It sells for around $40.00 and works great.

Kevin

---

