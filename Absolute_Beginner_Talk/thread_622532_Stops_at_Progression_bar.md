---
title: "Stops at Progression bar"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by maceintn on 2007-11-24
OK, here's what I have: (from Belarc Advisor)

Operating System 	  	System Model
Windows XP Home Edition Service Pack 2 (build 2600) 	  	HP Pavilion 061 PX744AA-ABA a1113w 0ny1211RE101Gold300
System Serial Number: 
Processor a 	  	Main Circuit Board b
2.93 gigahertz Intel Pentium 4
16 kilobyte primary memory cache
1024 kilobyte secondary memory cache 	  	Board: ASUSTeK Computer INC. Goldfish3 1.xx
Serial Number: 
Bus Clock: 133 megahertz
BIOS: American Megatrends Inc. 3.28 01/23/2006
Drives 	  	Memory Modules c,d
218.57 Gigabytes Usable Hard Drive Capacity
86.20 Gigabytes Hard Drive Free Space

LITE-ON DVDRW SOHW-1633S [CD-ROM drive]

Generic USB CF Reader USB Device [Hard drive] -- drive 4
Generic USB MS Reader USB Device [Hard drive] -- drive 6
Generic USB SD Reader USB Device [Hard drive] -- drive 3
Generic USB SM Reader USB Device [Hard drive] -- drive 5
MAXTOR 6L060J3 [Hard drive] (60.04 GB) -- drive 1
SAMSUNG SP1614C [Hard drive] (160.04 GB) -- drive 0
ST380011 A USB Device [Hard drive] (80.02 GB) -- drive 2 	  	1528 Megabytes Installed Memory

Slot 'DIMM1' has 512 MB (serial number SerNum0)
Slot 'DIMM2' has 512 MB
Slot 'DIMM3' has 256 MB
Slot 'DIMM4' has 256 MB
  	Local Drive Volumes
  	
		
c: (NTFS on drive 0) 	111.91 GB 	56.63 GB free
d: (FAT32 on drive 0) 	7.47 GB 	1.29 GB free
e: (FAT32 on drive 0) 	19.19 GB 	19.18 GB free
m: (FAT32 on drive 2) 	80.00 GB 	9.10 GB free
Controllers 	  	Display
Intel(R) 82801FB Ultra ATA Storage Controllers - 2651
Intel(R) 82801FB/FBM Ultra ATA Storage Controllers - 266F
Primary IDE Channel [Controller] (2x)
Secondary IDE Channel [Controller] (2x) 	  	Diamond S9250 PCI 256 DDR [Display adapter]
Diamond S9250 PCI 256 DDR - Secondary [Display adapter]
Intel(R) 82915G/GV/910GL Express Chipset Family [Display adapter]
HP D5259A [Monitor] (15.7"vis, s/n TH94818657, November 1999)
HP vs15 [Monitor] (14.6"vis, s/n CNC5201S9H, May 2005)
Bus Adapters 	  	Multimedia
Intel(R) 82801FB/FBM USB Universal Host Controller - 2658
Intel(R) 82801FB/FBM USB Universal Host Controller - 2659
Intel(R) 82801FB/FBM USB Universal Host Controller - 265A
Intel(R) 82801FB/FBM USB Universal Host Controller - 265B
Intel(R) 82801FB/FBM USB2 Enhanced Host Controller - 265C 	  	Riptide Audio Device
Riptide Bus / Firmware Downloader
Riptide Gameport
Riptide Input Device
Unimodem Half-Duplex Audio Device
Communications 	  	Other Devices
Agere Systems PCI Soft Modem
SoftV90 Voice Speakerphone Modem

		
1394 Net Adapter
Realtek RTL8139/810x Family Fast Ethernet NIC
 primary  	Auto IP Address: 	
	  	VIA OHCI Compliant IEEE 1394 Host Controller
CMS PortIO Driver
UltraMon Display Mirror Driver
HID-compliant consumer control device (2x)
HID-compliant device
USB Human Interface Device (2x)
Microsoft USB Dual Receiver Wireless Keyboard (IntelliType Pro)
HID-compliant mouse
USB Composite Device
USB Mass Storage Device (2x)
USB Printing Support
USB Root Hub (5x)
Virus Protection [Back to Top] 	 
ZoneAlarm Security Suite Antivirus Version 7.0.337.000
    Realtime File Scanning On
	 
1)Downloaded the i386 iso, verified the checksum(ok), burned to cd(at 4x), restarted, can't remember all the details here but I think it got to the UBUNTU title screen with a progression bar. It hung about 1/5 of the way!

2)Downloaded the alternative iso, verified..., burned..., restarted, did some repartitioning to get what Belarc reports above, then when I try to boot to Ubuntu, it displays the Ubuntu title with the progression bar, and yes, it hangs 1/5 of the way through!.....Also, I get a floating small white window that says something about resetting the display to 1024x768x60hz.

I'm new to linux. I'm wondering if this is a BIOS problem? OK, where do I start?

---

### Post by candtalan on 2007-11-25
Guessing it may be a display related problem - are you choosing the safe graphics mode of booting up choice? With one of my machines, things would just hang if a graphics item was unavailable or incorrect, but with safe graphics mode boot up, - although it still did not lead to a normal desktop GUI though it did get me to a terminal line where I could edit the system (if necessary with crtl-alt F1) and in my case edit the name of the graphics driver in  the file 
/etc/X11/xorg.conf
I have been using linux a while now but if I had needed to do that as a newcomer I would have been stumped though.

---

### Post by maceintn on 2007-11-26
> **candtalan said:**
> Guessing it may be a display related problem - are you choosing the safe graphics mode of booting up choice? With one of my machines, things would just hang if a graphics item was unavailable or incorrect, but with safe graphics mode boot up, - although it still did not lead to a normal desktop GUI though it did get me to a terminal line where I could edit the system (if necessary with crtl-alt F1) and in my case edit the name of the graphics driver in  the file 
/etc/X11/xorg.conf
I have been using linux a while now but if I had needed to do that as a newcomer I would have been stumped though.

Hi, thanks for replying. I was offline for awhile, so I'm just now getting to this.

I tried the second option,"Ubuntu Recovery." It progressed through a sequence of lines like this:
[53.679259][(can't remember what was here)] work_notifysig+0x13/0x25
[53.679358]=====================================

then hung!  I can't get to Linux. Is there something I can do within the Grub boot menu? Is there possibly something in my BIOS set wrong?

I should mention that I have tried to Ubuntu and Suse before with similar problems. also Partition Logic wouldn't start up either. I'm stumped! Point me to what ever I need to read and I'll do it but I don't even know what to ask at this point.

Thanks for any help.

---

### Post by candtalan on 2007-11-26
The recovery mode may not be very useful until you are more experienced perhaps. 
As I mentioned, if it is a graphics adapter issue - you seem to have at least an  ATI Diamond graphics card, and I recall there are some possible problems with ATI stuff - then (I am still guessing) then trying the 'Safe graphics' boot option from the menu in the live C D might show something. If you get to a command line rather than just a freeze then it is useful.

What version of Ubuntu are you using? If it is the latest (7.10) then it might be worth also trying an earlier version as a test.
If I am correct in thinking you have ATI graphics card, and also a further guess that the  problem is actually with that, then:
the multimedia and video section in theses forums will maybe get more expert help than I can offer, see 
 [http://ubuntuforums.org/forumdisplay.php?f=138](http://ubuntuforums.org/forumdisplay.php?f=138)
there are also comments about ATI drivers there too. I do not know if the problems would stop the show completely or just be not optimal though.

Another thought:
If the hardware works in xp (?) then it is unlikely to be your bios, anyway the CDs begin booting ok dont they? And you have used more than one CD.
Is there anything you know is unusual about the graphics hardware - I see that you have in the list *two* display lines:
Diamond S9250 PCI 256 DDR - Secondary [Display adapter]
Intel(R) 82915G/GV/910GL Express Chipset Family [Display adapter]
I wonder if the information is getting confused.  I had a case recently where there was on board graphics and also a graphics pci card also, the Bios setting for graphics adapter was set correctly (to auto) yet the pci graphics card was in use and the problem came when the Live CD received incorrect information from the bios. Anyway the graphics driver appearing in the file
/etc/X11/xorg.conf was the wrong one. (Use of safe graphics mode was one way to proceed, but it needed command line editing)
hth

---

### Post by Am3ndment on 2007-11-26
Sorry, for waking up old post, but...

I have similar problems, BUT i found way to "fix" that, try to boot your ubuntu, and use older kernel, and you will get forward :) Next time you boot, you should be able to use newer kernel. Hope that it helps :)

---

### Post by maceintn on 2007-11-29
> **Am3ndment said:**
> Sorry, for waking up old post, but...

I have similar problems, BUT i found way to "fix" that, try to boot your ubuntu, and use older kernel, and you will get forward :) Next time you boot, you should be able to use newer kernel. Hope that it helps :)

Hello,

Please don't consider this an old issue! I've been very busy with my two jobs, etc., so I haven't had time to work on this.

Let's see, where did I leave off? 1) I tried V.7.04 and got the same problem, the progression bar stops 1/5th way through!

Well, off to work I go.

---

### Post by klein de usa on 2007-12-13
hi 
i'm having the same problem with the same card but in two different dell's, i was blaming it on dell and there pci mb's, if you put the diamond cd in your computer and look at it in xp,(don't let it auto run!!!!) under drivers there is a file for linux, gives web sight files:

ati-driver-installer-8.19.10-i386.run 
ATI Proprietary Linux Release Notes.htm
fglrx_4_1_0-8.19.10-1.i386.rpm
fglrx_4_2_0-8.19.10-1.i386.rpm
fglrx_4_3_0-8.19.10-1.i386.rpm
fglrx_6_8_0-8.19.10-1.i386.rpm
Frequently Asked Questions about the ATI Proprietary Linux Driver.htm

i also found out that on the two systems ubuntu 7.10 i was trying to install that get-edid wasn't installed, and how i found that out is i booted edubuntu 7.10 cd and let it crash and it gave me the error about get-edid also it gave me the out put file from the xserver and ubuntu doesn't know what to do with this card it finds it but can't install it,

what i do is install ubuntu with the on board video then put in a pci video card and let it crash the x server then the x server gives me the error file and then i rebuild the x server but! but! but! i can't seem to crash the x server with ubuntu 7.10 it just hangs after rc.local. i haven't had time to fully look at the cd and i'm not sure if i know what to do with it but what is the worst i can do? crash it again!!!!!!!!!!!!!!!

---

### Post by klein de usa on 2007-12-13
i found this, it looks good 

[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html]("http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html")

---

