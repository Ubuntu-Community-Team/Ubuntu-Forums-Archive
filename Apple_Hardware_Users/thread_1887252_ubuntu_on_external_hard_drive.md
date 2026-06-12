---
title: "ubuntu on external hard drive"
date: 2011-11-26
forum: Apple Hardware Users
---

### Post by raleigh22 on 2011-11-26
i just bought a 750GB external hard drive and Im using it for my macbookair.  i want to dual boot ubuntu by saving it on the external hard drive.  i followed these instructions [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
when i was in the ubuntu trial desktop i tried to partition it to 50GB on my extrnl hdd, but all that showed up was the internal hard drive which has almost no room (hence my need for external hard drive).  how do i install ubuntu on the external hard drive? google results said you have to disconnect your internal hard drive but thats not possible on MBA.  thank you in advance.

---

### Post by raleigh22 on 2011-11-27
UPDATE: i installed it using this site: [http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
but when i was downloading it it said that a fatal error has occurred and the boot loader failed to install correctly.  It suggested either loading to a different disk or manually installing it.  I selected to install manually.  Any thoughts on how to manually install boot loader?

---

### Post by pindar on 2011-11-27
> **raleigh22 said:**
> UPDATE: i installed it using this site: [http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
but when i was downloading it it said that a fatal error has occurred and the boot loader failed to install correctly.  It suggested either loading to a different disk or manually installing it.  I selected to install manually.  Any thoughts on how to manually install boot loader?
I'm pretty sure that this will not work for a Macbook (or any other apple computer). They need an external disk with a GPT partition table to boot off, and they will only be able to boot in EFI mode. The guide you linked to is for generic PC hardware that is able to boot in BIOS mode from MBR partitions.

---

### Post by raleigh22 on 2011-11-27
I think it all worked except for the bootloader.  When i boot from a CD it now gives me the option to update ubuntu 11.10 to 11.10 or reinstall ubuntu 11.10.  SO i dont think it completely failed its just the boot loader that didnt work?  anyways if it didnt i now need a way to download ubuntu onto an external hdd from an apple computer.

---

