---
title: "PCI USB 2.0 Card not read in vmware for Windows XP"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by nandog on 2006-08-18
Hello all, I am new to this forum and i have a problem with a PCMCIA usb 2.0 card being read for vmware. When i put it into the pci slot of my laptop while running vmware it is not detected. The problem arises when i place my usb 2.0 flash drive into one of the usb slots for the card, and in vmware (windows XP) it gives me a response saying that i'm running a high speed usb device in a non high speed usb port. I'm assuming it is reading my pci card as a USB 1.1 card. Any help is appreciated :) I dont know if the problem is caused by Ubuntu not reading my pci card as a usb 2.0. Thanks

---

### Post by anaconda on 2006-08-18
When windows is run through WMVare it uses hardware through ubuntus drivers.. 

so I suggest that you put the PCMCIA card in before you even start VMWare, so that ubuntu (and VMWare) regognizes it properly.

But I have heard that others have also had problems with VMWare using (nonPCMCIA)USB 2.0 ports as USB 1.1 ports.. dont know the solution to that.. sorry.

---

