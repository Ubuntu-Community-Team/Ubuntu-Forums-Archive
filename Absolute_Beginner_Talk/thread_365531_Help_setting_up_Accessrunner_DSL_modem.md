---
title: "Help setting up Accessrunner DSL modem"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by cknight on 2007-02-19
Well, I've proudly made it this far, a pure linux newb having installed Kubuntu (Edgy) as a dual boot beside XP.  However, I'm at wits end trying to make my Intel PRO/DSL 2100 modem work.  

Here's what my lspci looks like:

00:0b.0 System peripheral: Conexant ADSL AccessRunner PCI Arbitration Device (rev 01)
00:0b.1 ATM network controller: Conexant AccessRunner PCI ADSL Interface Device (rev 01)


I've found many posts and resources related to getting the AccessRunner chipset working, but these seem mainly aimed at USB modems, unlike the PCI one that I have.  In particular, [https://help.ubuntu.com/community/UsbAdslModem/AccessRunner](https://help.ubuntu.com/community/UsbAdslModem/AccessRunner) suggests that I can extract the firmware from the driver using a utility maintained by [http://accessrunner.sourceforge.net/modems.shtml](http://accessrunner.sourceforge.net/modems.shtml).  However, I can't find the CnxEtU.sys file anywhere on my install CD or in the windows driver folder.  Instead, according to Windows Device manager, I've got two drivers installed for the modem:  CnxTgN.sys and CnxTgP.sys.  

Running the cxacrufw utility on them fails as it can't find the firmware start sequence.

I've also seen [http://patrick.spacesurfer.com/linux_conexant_pci_adsl.html](http://patrick.spacesurfer.com/linux_conexant_pci_adsl.html) which suggests all kinds of things way over my head along with the suggestion in bold that this is not for novices... But I'm willing to learn if someone can help decipher in simple terms/steps exactly what it is I need to do.

Can anyone give me a high level description of what it is Patrick's site is proposing? Do I need to do all the steps (my kernel version is 2.6.17)?  Do you think a novice like me could tackle such an installation (not that I've much to lose!)?

Thanks so much in advance!

---

