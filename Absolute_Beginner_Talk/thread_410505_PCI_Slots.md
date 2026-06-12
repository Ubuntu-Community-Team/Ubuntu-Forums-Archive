---
title: "PCI Slots?"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2007-04-15
I am interested in adding a graphics card to my computer to use in place of the integrated card that is there now.  According to my friend, all I need to do is have a free PCI slot and then pop in a video card.  Is there a command for discovering available PCI slots from the terminal?

---

### Post by trent dillman on 2007-04-15
...

---

### Post by Darklighter137 on 2007-04-15
This is the output it gave me:
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a33 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Communication controller: Conexant HSF 56k Data/Fax Modem
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

I don't know a terrible lot about hardware...  Are there free slots?

---

### Post by jem7v on 2007-04-15
...or instead of trying to find some command that tells you how many free/empty PCI slots you have, you could just open up your computer case and Look... :)
[http://images.tigerdirect.com/itemdetails/A455-1056/A455-1056COUT.jpg](http://images.tigerdirect.com/itemdetails/A455-1056/A455-1056COUT.jpg) shows a labeled motherboard so you know what a PCI slot is.

If you have an AGP slot you could use an AGP graphics card, and if you have a PCI-E (PCI-Express) slot you could use a PCI-E card... but if you have neither, you'll just have to go with a regular ol' PCI card.

---

### Post by Maestro23 on 2007-04-15
> **jem7v said:**
> ...or instead of trying to find some command that tells you how many free/empty PCI slots you have, you could just open up your computer case and Look... :)
[http://images.tigerdirect.com/itemdetails/A455-1056/A455-1056COUT.jpg](http://images.tigerdirect.com/itemdetails/A455-1056/A455-1056COUT.jpg) shows a labeled motherboard so you know what a PCI slot is.

Beat me to it.  Why make things hard.:D

---

### Post by Darklighter137 on 2007-04-15
Thanks guys!

So, any slots like that will work?  I mean, there isn't a speciail "graphics card goes here slot" or anything like that?  Sorry, I'm a total newbie to adding new hardware. =(

---

### Post by jem7v on 2007-04-15
AGP slots are exclusively for graphics card; I think the same goes for PCI-E.  Other than that, it doesn't really matter which slot a PCI card goes in... though if you're an old timer like me, you might avoid putting 2 PCI cards in adjecent slots.  (The most practical reason is it gives them better ventilation if there's more space between them, and it's easier if you don't have small hands.  Also, superstition.)

---

### Post by Darklighter137 on 2007-04-15
Awesome, thanks!  ^_^

---

### Post by Razorback on 2007-04-15
Is your motherboard new or is it older?  If an AGP slot is available, it will be the closest slot to the power supply and is usually a different color - it is brown on mine.

---

### Post by milton1 on 2007-04-17
> **jem7v said:**
>  Other than that, it doesn't really matter which slot a PCI card goes in... 

Many systems will require that a pci video card be placed in the first PCI slot, or at least before any other cards.

---

