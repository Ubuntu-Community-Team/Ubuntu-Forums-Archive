---
title: "AsRock Z77 pro3 compatible with linux? and can I install GeForce 650 Ti on it"
date: 2013-04-19
forum: Any Other OS
---

### Post by snowlizard31 on 2013-04-19
I bought an AsRock Z77 pro3 motherboard for the computer I plan on building; I have a few questions though can I run Linux OS's on it specifically Linux Mint. Also can I install a Nividia Geforce 650 Ti BOOST as the GPU, Does it have a wireless card or do I have to buy one? This is my first build so any tips and help will be greatly appreciated.

---

### Post by oldfred on 2013-04-19
Know nothing about Mint, moved to other OS.

You would have to look at specifications of motherboard to see if it includes wireless. 

You can add nVidia cards, but with Ubuntu you need nomodeset. 

You have UEFI but can install in legacy/BIOS/CSM. If dual booting with Windows you need both in UEFI or both in BIOS mode.
If not installing Windows best to have drive partitioned with gpt whether UEFI or BIOS and have both an efi partition (if UEFI or future use) and bios_grub if BIOS boot. But Windows will only boot from gpt drive if UEFI.

 UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)

---

### Post by snowlizard31 on 2013-04-19
whats the purpose of nomodeset? would I have to erase quiet splash from the boot options or add both nomodeset and quiet splash?
If I'm installing both on the same HDD I should install windows first right?

---

### Post by oldfred on 2013-04-19
If you are installing Windows you have to decide up front if you want BIOS/MBR or UEFI/gpt. Windows only boots from gpt partitioned drives with UEFI.
UEFI is new, not many really know it yet but it is the future. It does have some advantages. But even motherboard vendors are still making regular fixes.
BIOS is old about 30 years old, MBR has 4 primary partition limit, but everyone now understands it well and it has few bugs. But newer hardware has pushed the limits of what BIOS can do.

Install Windows first. And use Windows disk tools to shrink the Windows partition. Reboot Windows a couple of times to let it run chkdsk and make its repairs to its new size.

The nomodeset is required with nVidia, I normally replace quiet splash to see boot process in case something else has issues and needs additional boot parameters.

How you boot both Windows and Ubuntu is how it installs. Windows only installs in UEFI mode from flash drive. Ubuntu will install in either BIOS or UEFI mode to gpt partitioned drive, so if Windows is UEFI be sure to boot Ubuntu in UEFI, or if Windows if BIOS/MBR be sure to boot Ubuntu in BIOS mode.

---

### Post by mips on 2013-04-20
You will have to buy a wireless card/dongle.

Linux will work on it.

---

### Post by snowlizard31 on 2013-04-21
Thanks guys now I'll know what to do when I make the partitions. Another question if I may though; what kind of wireless should i get and where can I get it because I can't seem to find them on newegg.com

---

### Post by mips on 2013-04-22
> **snowlizard31 said:**
> ...I can't seem to find them on newegg.com

[http://www.newegg.com/Wireless-Adapters/SubCategory/ID-31?&cm_sp=Networking281-_-VisNav-_-WirelessAdapters](http://www.newegg.com/Wireless-Adapters/SubCategory/ID-31?&cm_sp=Networking281-_-VisNav-_-WirelessAdapters)

Select interface type on the left. Before buying ensure chipset is well supported by linux.

---

### Post by snowlizard31 on 2013-04-22
Am I supposed to buy a card with the little antennas? sorry if it sounds like a stupid question I just though wireless cards would be more card shaped especially for a desktop

---

### Post by oldfred on 2013-04-23
In the old days the FCC required computers to be totally shielded so not radio interference would happen. I remember some of the early one's used to interfere with my nearby radio. They had two specs one business & one home.
So an internal card only may not work. 

After the issues on the iphone we learned its antenna is built into the edge of the case to better receive signals.

---

### Post by mips on 2013-04-23
> **snowlizard31 said:**
> Am I supposed to buy a card with the little antennas? sorry if it sounds like a stupid question I just though wireless cards would be more card shaped especially for a desktop

Your case is a metal box, not good for signal propagation hence the antennas...

---

### Post by snowlizard31 on 2013-04-23
That makes sense Thanks for the help man and Thank you Oldfred

---

