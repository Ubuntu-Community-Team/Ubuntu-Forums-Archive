---
title: "Dual Boot with WinServer 2003, SIIG ATA PCI Card"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by HammerNJ on 2008-01-08
Hi:

Figured this is the best place to post this. Tried to install 7.10 from the Alternate CD on my old HP Pavilion 7915 with a SIIG SATA PCI Card and a Barracuda SATA 320GB Disk. Had to put jumpers on the drive to slow it down to 1.GB per second to match the Card. Booted from CD and got up to Drive Partitoning, then locked up. Tried about 4 times. Gave up and installed Win 2003 Server (had to use SIIG Driver Floppy during install, no Linux drivers, grrrr)

Now I'd like to install 7.10 so I can Dual Boot and test Windows apps when only absolutely necessary. 
I'm sure someone has done this before but I couldn't find any relative posts. 

Thanks, Hammer

---

### Post by dcstar on 2008-01-08
> **HammerNJ said:**
> Hi:

Figured this is the best place to post this. Tried to install 7.10 from the Alternate CD on my old HP Pavilion 7915 with a SIIG SATA PCI Card and a Barracuda SATA 320GB Disk. Had to put jumpers on the drive to slow it down to 1.GB per second to match the Card. Booted from CD and got up to Drive Partitoning, then locked up. Tried about 4 times. Gave up and installed Win 2003 Server (had to use SIIG Driver Floppy during install, no Linux drivers, grrrr)

Now I'd like to install 7.10 so I can Dual Boot and test Windows apps when only absolutely necessary. 
I'm sure someone has done this before but I couldn't find any relative posts. 

Thanks, Hammer

If Ubuntu won't support that hardware then leave Windows on it and install vmware server (it is free), then you can install and run Ubuntu inside a VM on top of Windows.

It should run reasonably well as it could on such old hardware.

---

### Post by HammerNJ on 2008-01-10
Hi David:

Thanks for the reply. I love VMWare and own Workstation, it is an absolute requirement in my tool kit.

I know I can run Server on the HP POS but I wanted to avoid virtualization 'cause the HP has less than a gig of RAM (640MB to be exact) and I'm afraid it will run like molasses going uphill in January. 

Ever hear of someone writing a driver for the SIIG PCI SATA Card?

Thanks, Seth

---

### Post by roadrocket13 on 2008-01-10
i'm having similar issues. my Siig PCI IDE expansion slot doesn't like to work either. try this ....


the chipset used is a Silicon Image SiI3112
driver name: sata_sil

[http://linux-ata.org/driver-status.html#sii311x](http://linux-ata.org/driver-status.html#sii311x)

---

### Post by HammerNJ on 2008-01-15
'm having similar issues. my Siig PCI IDE expansion slot doesn't like to work either. try this ....


the chipset used is a Silicon Image SiI3112
driver name: sata_sil

[http://linux-ata.org/driver-status.html#sii311x](http://linux-ata.org/driver-status.html#sii311x)

>>>>>>>>>>>>>>>>>>>

Thanks for the above. Pardon my noobiness, but is this a downloadable .deb package? How do you use it during install? 

Thanks, Seth

---

