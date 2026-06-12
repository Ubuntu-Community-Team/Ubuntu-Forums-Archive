---
title: "screen resolution resizing"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by rwarwarwa on 2008-01-23
Hi there,

I want to optimize my screen resolution but I only have the choice of 800x600 or 640x480. Why is there no option to increase it past that?

thanks,

rwa

---

### Post by kpkeerthi on 2008-01-23
What graphics card do you have? If you are unsure, post the output of ```
lspci
``` command.

---

### Post by rhc on 2008-01-23
> sudo gedit /etc/X11/xorg.conf

Type this.
> 
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"F700B"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"640x480"
	EndSubSection

From this section add your resolution to the modes.

(If you already installed drive for graphic card)

---

### Post by rwarwarwa on 2008-01-23
thanks

rwa@rwa-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
01:09.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
01:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
01:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
01:0b.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev 10)
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
rwa@rwa-ubuntu:~$ 
rwa@rwa-ubuntu:~$

---

### Post by rhc on 2008-01-23
Thanks and so?
Did  you solved it?

---

### Post by kpkeerthi on 2008-01-23
Install the new Intel Driver.
[https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28resolution%29%7C%28video%29#head-b26796d178114bd3fdea5600480d8ab3137274d1](https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28resolution%29%7C%28video%29#head-b26796d178114bd3fdea5600480d8ab3137274d1)

---

