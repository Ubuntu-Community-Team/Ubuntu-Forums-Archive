---
title: "How to check whether i have Intel Graphics driver (i810)"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by umairsaeed219 on 2007-07-01
i want to cinfigure my monitor resolution and refresf rate for this purpose i want to know whether i have Intel Graphics driver (i810)or some other version i required this info because  i want to act upon the instruction of this post [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by overdrank on 2007-07-01
> **umairsaeed219 said:**
> i want to cinfigure my monitor resolution and refresf rate for this purpose i want to know whether i have Intel Graphics driver (i810)or some other version i required this info because  i want to act upon the instruction of this post [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Hi and welcome, it gives you the command to use in the terminal  to view your xorg file 
[PHP]sudo nano /etc/X11/xorg.conf[/PHP]
However I would recommend using 
[PHP]gksudo gedit /etc/X11/xorg.conf[/PHP]
If you scroll down to the devices section you should see your graphics card name there and be low it will be the driver then the screen section below it will have the resolution. 
For example here is mine.
[PHP]
Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection
[/PHP]
I hope this helps and good luck!

---

### Post by umairsaeed219 on 2007-07-01
actually i want to install Intel Graphics driver (i810) on my pc which has currently VESA  driver 
i just want to make sure that i810 can be installed on my pc iam currently running  7.04
following are results of lspci which might help you to guide me whether i can install i810 or not

[PHP]umair@umair-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:01.0 Communication controller: Intel Corporation 536EP Data Fax Modem
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)[/PHP]

---

### Post by umairsaeed219 on 2007-07-01
hey guys i have successfully got my required resolution on my  intel 845 

First of all i put the 6.06 cd in cd rom because at that time i have simply configured xserver and i was able to get my required resolution back si for the sake of comparing the settings of 6.06 with 7.04 i have put the cd in cd rom and boot from cd Rom 
When GUI comes u with option to install 6.06 on system i simply run the following command
> sudo dpkg-reconfigure xserver-xorg
i write down all option selected by default by ubuntu 
for examole 
it has selected i810 in option attempt  to auto detect video hardware(in 7.04 it was VESA by default)

then in option enter identifier if your video card i write down the option which was by default selected by 6.06
it was 
> Corporation 81845G/GL[Brookdale-G]/GE Chipset Integerated Graphics Device
so i have pasted the same line while configuring xserveer on 7.04
then i leave all option as it is except write 
horizontal sync and vertical sync (please write according to your monitor specifications)
then i restart x server and it worked
now i can choose my required resolution 800x600 @85 hz

---

