---
title: "SD Card reader for Toshiba not working."
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by stevelasvegas on 2007-05-27
Can anyone help me please?
I have a Toshiba M-55 S-3294 laptop. When I insert an SD card in the built in reader, the reader light keeps blinking but is not recognized.
I am using Ubutu Feisty 7.04.
This is what I get when I run a driver check.
Debian GNU/Linux device driver check page
PCI ID	Works?	Vendor	Device	Driver	Comment
80862590	Yes	Intel Corporation	Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller	intel-agp,agpgart	 
80862592	Yes	Intel Corporation	Mobile 915GM/GMS/910GML Express Graphics Controller	intelfb,i810	 
80862792	Yes	Intel Corporation	Mobile 915GM/GMS/910GML Express Graphics Controller	i810	 
80862660	-	Intel Corporation	82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1	 	 
80862658	Yes	Intel Corporation	82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1	usb-uhci,uhci-hcd	 
80862659	Yes	Intel Corporation	82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2	usb-uhci,uhci-hcd	 
8086265a	Yes	Intel Corporation	82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3	usb-uhci,uhci-hcd	 
8086265b	Yes	Intel Corporation	82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4	usb-uhci,uhci-hcd	 
8086265c	Yes	Intel Corporation	Dimension 3100	ehci-hcd	 
80862448	Yes	Intel Corporation	82801 Mobile PCI Bridge	i810_rng,hw_random	 
8086266e	Yes	Intel Corporation	82801FB/FBM/FR/FW/FRW (ICH6 Family) AC97 Audio Controller97 Audio Controller	snd-intel8x0,i810_audio	 
8086266d	Yes	Intel Corporation	82801FB/FBM/FR/FW/FRW (ICH6 Family) AC97 Modem Controller97 Modem Controller	snd-intel8x0m	 
80862641	Yes	Intel Corporation	82801FBM (ICH6M) LPC Interface Bridge	intel-rng,i8xx_tco	 
80862653	Yes	Intel Corporation	82801FBM (ICH6M) SATA Controller	ata_piix,ahci	 
8086266a	Yes	Intel Corporation	82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller	i2c-i801	 
11ab4351	Yes	Marvell Technology Group Ltd.	88E8036 PCI-E Fast Ethernet Controller	sky2	 
80864220	Yes	Intel Corporation	PRO/Wireless 2200BG Network Connection	ipw2200	 
104c8031	Yes	Texas Instruments	PCIxx21/x515 Cardbus Controller	yenta_socket	 
104c8032	-	Texas Instruments	OHCI Compliant IEEE 1394 Host Controller	 	 
104c8033	-	Texas Instruments	PCIxx21 Integrated FlashMedia Controller	 	 
104c8034	Yes	Texas Instruments	PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller	sdhci	 

Thank You

---

### Post by stevelasvegas on 2007-05-27
Found the solution.
[https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/6262](https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/6262)
For any others who might have the same problem.:)

---

### Post by chudder on 2007-07-31
this did work, it didn't have all the right outputs but I put in my card and it worked.  Thanx for the direction, I've been trying to get it working for some time now to no avail until now.  

Thanx

Chud

---

