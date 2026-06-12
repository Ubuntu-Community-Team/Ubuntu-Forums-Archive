---
title: "SATA IDE Motherboard boot issue solved"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by cdenk on 2008-02-24
I have a Intel D965-LT motherboard with dual boot Win XP Pro that has one IDE (2 drives) and 4 SATA ports, but have 2 harddrives and 2 DVD drives, all IDE. After setting Bios to various settings, found it was not possible automatically to boot from something other than the one motherboard IDE connector. 

Tried first a Startech SATA2ATA133 adapter that piggybacks on the back of an IDE drive and SATA cable then to motherboard. It was possible to boot from a DVD, but required F10 to get a boot menu. Then tried a Startech PCIIDE2 card (PCI to mother board> 2 IDE (2 drives each)) with similar results. A call to Startech tech support (corporate land line and then "4") resulted in a very helpful and knowledgeable person located in central Ohio. Recommendation was to get a Startech PCIIDE100R 2 channel raid card that had a boot rom, and didn't have to use the raid. Ordered from CDW, received and installed. In XP PRO unable to install the driver. Another call to Startech, and while on the phone, a custom driver was E-mailed and works. CDW has issued a RMA for the one card, it should be there UPS in a day.

Just a newbie to Linux, Kubuntu Gutsy seems to be handling all drives OK. Haven't had the opportunity to try writing yet, but insert a CD and Kubuntu is asking how to handle the CD. :)

---

