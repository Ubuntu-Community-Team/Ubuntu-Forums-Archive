---
title: "eMachines eOne thread:"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by livinginx on 2007-01-08
So, my manager just gave me an eMachines eOne 433 the other day.  Didn't tell me the password for Windows, so I just said screw it and installed Xubuntu on it.  Typical step for me, since I already have Edgy installed on both my main comps.

*I have the 433mhz version, so I don't have all of the details about the 500mhz version.  If somebody could post their info for everybody, that would be nice.
**Also, I have 192MB ram installed (64+128MB) so, results may differ.

***Specs:***
Proc: Celeron 433mhz / 500mhz
Ram: 64MB onboard (w/ available pc100/133 laptop memory slot for upgrading)
Graphics: ATI Rage XL w/8MB ram (AGP 2x, but not AGP slot)
Monitor: 15" (14" Viewable) SVGA
HDD: 6.4GB  / 8.4GB (uDMA IDE)
CD-Rom: 24x Slim CDRom
Host bridge: Intel 440LX/EX - 82443LX/EX
PCI bridge: same as host
ISA bridge: Intel 82371AB/EB/MB PIIX4
IDE bridge: same as ISA
USB bridge: same as ISA/IDE
Audio: Cirrus Logic CS 4614/22/24
Cardbus bridge (x2): TI PCI1225
Modem: PCTel Inc HSP MicroModem 56 (56k)
Ethernet Controller: Intel 10BaseT w/home PNA (LSPCI lists as: Intel 21145)(Doesn't have --100BaseT)
-=-=-=-=-=-
#Rundown#
Xubuntu 6.06 installed no problems albeit a bit slow.

Problem (might just be me), when I plug the NIC into the router, I get no lights.  NIC Shows up in Networking, but I can't figure this one out.

-=-=-=-=-=-
#   Future   #
Trying to get NIC working 100%
Trying to get the console buttons working
Testing all inputs (USB, A/V in, audio inputs, etc.)
Figure out how to cut the flicker down on the monitor

----------------
Please post your results as I am sure there are a few other people that have these things stuffed in a closest or see one at a garage sale.

---

### Post by yager on 2007-01-08
Was the network card installed when you installed Xubuntu?  If not, then its possible Xubuntu did not provide the driver so the card is not being used.  Put the LiveCD in the system and boot from it with the Network card installed to see if if configures the card automagically.  Otherwise, you will have to find out what kind of card it is and hunt for a driver.  Unlikely though.

There is also the possibility the card is dead if it was old or used.

---

### Post by livinginx on 2007-01-08
Yeah, I had the card enabled in the bios. It's built into the mobo.  The eOne is an all-in-one type of unit, got shutdown by Mac cause it is an IMac clone.

I will double check the LiveCD part with a couple of BIOS options changed.

*** EDIT ***
No go

Somehow, I think the problem has to do with the fact the card is originally supposed to be 10/100, but they pulled the 100BaseT controller out and put in the Home PNA crap.  But it won't show lights on the router or the switch in known working ports, with known working cables.  So either it is because of the chip or because it is old and dead.

---

### Post by yager on 2007-01-09
That is a bummer on the network port.  Is there any room to install cards inside?  Maybe you could disable the onboard and go with a second card.  Or maybe if it has a USB port, you could try something like this.

[http://www.usbgear.com/computer_cable_details.cfm?sku=205184&cats=112&catid=112](http://www.usbgear.com/computer_cable_details.cfm?sku=205184&cats=112&catid=112)

At $26.50 it is not too much but I realize it sure would be nice it will work before getting it.  There is always eBay, or asking to borrow something like this from a local computer shop.

---

### Post by livinginx on 2007-01-10
The only upgrade slots on the eOne are PCMCIA and the laptop ram slot.

So, unfortunately, I tucked in the closet cause I got a new toy today.  I got an xSeries IBM :-D  So happy, but I will still help people with eOne's if needed.

---

### Post by livinginx on 2007-01-16
Alright, I am thinking about dropping a PCMCIA wired card in.  Tigerdirect has one on sale for about $17 (US) [TrendNet PCMCIA]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=308770&CatId=0")
and another for a bit more.

Just wondering if anybody has had any luck with these in Linux?

---

