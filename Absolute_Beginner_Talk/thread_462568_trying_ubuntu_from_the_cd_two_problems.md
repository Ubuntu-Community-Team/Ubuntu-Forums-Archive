---
title: "trying ubuntu from the cd two problems"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by tony404 on 2007-06-02
It showed my wireless connection but wouldnt let me to connect to it, what am I doing wrong. Also my resolution wont go any higher then 800x600. Any help would be great if I can fix those two Im going to install, liked everything I saw.

---

### Post by Lucifiel on 2007-06-02
What's your system specifications? I'm not too sure about the resolution issue but for wireless, you can try ndiswrapper, only that it wasn't included with the Feisty cd.

---

### Post by Lucifiel on 2007-06-02
Also, which livecd are you using? 7.04(Feisty fawn) or...?

---

### Post by tony404 on 2007-06-02
im using feisty fawn, i thought the wifi thing was weird. I always thought that if it sees it i assumed you could connect to it.

---

### Post by Lucifiel on 2007-06-02
Hullo. You still have not given your system specifications. If you won't give it, then we can't help you.

---

### Post by bobplano on 2007-06-02
you could try the command
```
sudo dpkg-reconfigure xserver-xorg
```
but hardware specs would give a more specific answer

---

### Post by tony404 on 2007-06-02
how do I get the hardware specs?

---

### Post by diatribe on 2007-06-02
lshw will work

---

### Post by tony404 on 2007-06-02
Windows XP Home Edition Service Pack 2 (build 2600) 	  	Gateway Gateway 400VTX Rev 1
System Serial Number: 0031715078
Enclosure Type: Notebook
Processor a 	  	Main Circuit Board b
2.20 gigahertz Intel Mobile Pentium 4 - M
8 kilobyte primary memory cache
512 kilobyte secondary memory cache 	  	Board: Gateway Gateway 400VTX Rev 1.0
Bus Clock: 400 megahertz
BIOS: Gateway 38.00.35 03/12/2003
Drives 	  	Memory Modules c,d
80.02 Gigabytes Usable Hard Drive Capacity
54.64 Gigabytes Hard Drive Free Space

QSI CDRW/DVD SBW-242 [CD-ROM drive]

FUJITSU MHV2080AH [Hard drive] (80.03 GB) -- drive 0, s/n NT62T6325TA2, rev 000000A0, SMART Status: Healthy
USB2.0 CardReader CF RW [Hard drive] -- drive 1
USB2.0 CardReader Combo [Hard drive] -- drive 2 	  	1016 Megabytes Installed Memory

Slot 'DIMM 0' has 512 MB
Slot 'DIMM 1' has 512 MB
  	Local Drive Volumes
  	
		
c: (NTFS on drive 0) 	80.02 GB 	54.64 GB free
  	Network Drives
  	None detected
Users (mouse over user name for details) 	  	Printers
local user accounts	last logon
 

DISABLED Marks a disabled account;   LOCKED OUT Marks a locked account
	  	

Controllers 	  	Display
Intel(R) 82801DBM Ultra ATA Storage Controller - 24CA
Primary IDE Channel [Controller]
Secondary IDE Channel [Controller] 	  	Intel(R) 82852/82855 GM/GME Graphics Controller [Display adapter] (2x)
Default Monitor
Digital Flat Panel (1024x768) [Monitor]
Bus Adapters 	  	Multimedia
O2Micro OZ6912 CardBus Controller
Intel(r) 82801DB/DBM USB 2.0 Enhanced Host Controller - 24CD
Intel(R) 82801DB/DBM USB Universal Host Controller - 24C2
Intel(R) 82801DB/DBM USB Universal Host Controller - 24C4 	  	Realtek AC97 Audio
Communications 	  	Other Devices
		
Hawking Technologies HWUG1 Wireless-G USB Adapter w/Removable Antenna
 primary  	
	
 

Microsoft ACPI-Compliant Control Method Battery
HID-compliant consumer control device
HID-compliant device
USB Human Interface Device (2x)
Intel(R) Graphics Chipset (KCH) Driver
Intel(R) Graphics Platform (SoftBIOS) Driver
HID Keyboard Device
Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
HID-compliant mouse
Synaptics PS/2 Port TouchPad [Mouse]
USB Composite Device
USB Mass Storage (UISDMC30/32W) Device Driver
USB Root Hub (3x)
Virus Protection [Back to Top] 	 
Kaspersky Internet Security Version 6.0.2.621
    Realtime File Scanning On

---

### Post by Lucifiel on 2007-06-02
Hmmm... from some research, it says that 

> The Edimax(name corrected) 7318USg is re-packaged and sold in USA as the Hawking HWUG1. They are exactly the same unit, ie. identical FCC ID. You can find the Hawking HWUG1 at amazon.com and various other stores.

So, maybe you can try getting the Linux drivers for Edimax 7318USg and installing them for your Hawking HWUG1 device. 

[http://www.murrayc.com/blog/permalink/2007/02/17/linux-compatible-wireless-usb-adaptor-results/](http://www.murrayc.com/blog/permalink/2007/02/17/linux-compatible-wireless-usb-adaptor-results/)

Edit: But you likely can only install those drivers after you've installed Ubuntu since they likely require a restart of the pc.

---

### Post by Lucifiel on 2007-06-02
Oh and my suggestion is to try this:

download the linux drivers using Windows and then save them to a usb disk or floppy drive or something.

Because you're not going to be able to access the internet, so you need to work on this as soon as you install Ubuntu. Don't touch anything else until you've got your network working. Because if say, anything goes wrong, it's quite troublesome to boot from Ubuntu into Windows and back into Ubuntu again.

---

### Post by tony404 on 2007-06-03
thank you

---

### Post by Lucifiel on 2007-06-03
No problem.

My suggestion is also to try and find out the extension name of the drivers and see if they can be installed within Ubuntu or not. 

If you find a .deb file, usually it will work but take note there are 2 types of .deb files: 

.deb packaged for Debian(another Linux distribution) and
.deb packaged for Ubuntu

Sometimes, the Readme file for the drivers might mention this. Sometimes, not. 

.rpm = package for Red Hat Linux(another distribution) If you find this, you will need Alien to install it. But try and find a .deb package if you can. 

Good luck! :)

---

### Post by LouisvilleLIP on 2007-06-12
Good luck with the 400vtx 800x600 resolution issue.  I tried for a long time and gave up.  If you find a way to do it, post the solution, I couldn't confirm that anyone ever got higher resolutions working on the 400vtx

---

