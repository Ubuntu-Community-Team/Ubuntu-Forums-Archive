---
title: "Dual Boot - Gateway MT6840 - XP &amp; Ubuntu"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by lkraemer on 2007-12-26
The following information will assist you in locating and download the correct drivers, so you can 
downgrade the Gateway MT6840 from Vista to Win XP SP2.  There is an additional problem of the
MT6840 using a SATA Hard Drive, and Windows XP won't automatically detect the drive unless some
SATA drivers are slipstreamed onto the XP CD, a USB EXT Floppy is available to supply the Drivers
on floppy disk, or TEXTMODE Install is used.  These will be discussed later.

1.  Log into the Gateway Support Site and provide your serial # to get the XP drivers.
    Do NOT use a Model Number as they won't provide the files you need (they'll
    try to give you vista drivers).
    Gateway MT6840 Serial Number to get into Driver Downloads:

    T3C76H1024998   (Note: if your unit is Refurbished the model number won't allow access.)


	[http://support.gateway.com/support/drivers/mydl.asp?tab=MY&os=Windows%20XP](http://support.gateway.com/support/drivers/mydl.asp?tab=MY&os=Windows%20XP)

		     (Download and save to DVD or CDR's for reference later.)
		XP - BIOS - 7712.exe - BIOS Version 77.12 (Probably NOT needed)
		XP - SATA Hard Drive - D20035-001-001.EXE - Intel 6.2.0.2002 (Probably NOT needed)
		XP - Media Reader - D20003-003-001.EXE - Version TI 2.0.0.6 (MUST DOWNLOAD)  ****
		XP - Wireless Network - D00756-001-001.EXE - Intel Wireless Driver Version 11.1.0.86 (MUST DOWNLOAD)  ****
		XP - Network - D00750-002-001.EXE - Intel Network Driver Version 9.7.34.0 (Probably NOT needed)
		XP - Bluetooth - D00736-001-001.EXE - Gateway Widcomm Bluetooth Drivers (Probably NOT needed)
	        XP - Sigmatel Audio Drivers - D00560-002-001.EXE Version: 5.10.4946.0 (MUST DOWNLOAD)  ****
                     [http://support.gateway.com/support/drivers/getFile.asp?id=20598&dscr=Sigmatel%20Audio%20Driver%20Version:%205.10.4946.0&uid=167551212](http://support.gateway.com/support/drivers/getFile.asp?id=20598&dscr=Sigmatel%20Audio%20Driver%20Version:%205.10.4946.0&uid=167551212)

2.  Go to:
	[http://support.gateway.com/s/Mobile/2007/Oasis/1014554R/1014554Rsp2.shtml](http://support.gateway.com/s/Mobile/2007/Oasis/1014554R/1014554Rsp2.shtml)
	And review the Technical Specifications for the MT6840.

TEXT information file:	Add any additional information from CONTROL PANEL, SYSTEM, HARDWARE, DEVICE MANAGER.
MT6840 Notebook Specifications
Part Number: 1014554R	Gateway MT6840 Notebook

Feature 		Description
Processor 		Intel® Core&#8482; 2 Duo processor T2450
			2.0 GHz | 2 MB L2 cache | 533 MHz FSB

Chipset 		Intel® 945GM
			Device Manager info: 12/12/06 Driver ver 7.14.10.1147

Display panel 		15.4-inch WXGA (1280 × 800)

Memory 			1024 MB 667 MHz DDR2 SDRAM (2 × 512)
			Operates at 533 MHz
			Total slots: 2 DDR2 slots | Available slots: 0 DDR2 slots
			Maximum memory: 4 GB

Video controller 	Intel® Graphics Media Accelerator 950
			Up to 224 MB of shared video memory (when 512 MB or more system memory present)

Audio 			High definition audio - 2 channel
			Device Manager info: Sigmatel Audio

Hard drive 		160 GB 5400 RPM SATA hard drive
			Device Manager info: Segate ST9160821AS
			Device Manager info: Intel 82801G Controller
			Device Manager info: Intel 82801GBM SATA AHCI Controller
 
Optical drive 		8x Multi-Format Dual Layer DVDRW with DVD-RAM

			Write maximum: 8X DVD±R, 6X DVD-RW, 8X DVD+RW, 2X DVD-R DL, 2.4X DVD+R DL,
			5X DVD-RAM, 24X CD-R and 16X CD-RW discs
			Read maximum: 8X DVD-R/RW/ROM, 4X DVD±R DL, 5X DVD-RAM, 24X CD-R/RW/ROM discs 

Modem 			Integrated V.92 56K modem
			Device Manager info: Motorola SM56

Network 		10/100 Ethernet LAN
			Intel® PRO/Wireless 3945 802.11a/b/g
			Device Manager info: Marvell Yukon 88E8038 PCI-E LAN
			Device Manager info: Intel 3945ABG Wireless 

Memory card reader 	4-in-1

			    * Memory Stick®
			    * Memory Stick Pro®
			    * Multimedia Card&#8482;
			    * Secure Digital&#8482;

			MiniSD and RS-MMC (when used with adapter that is supplied with card) 
			Device Manager info: TI PCIxx12 Flash Media Controller

I/O ports 	
			    * Four - USB 2.0 ports
			    * One - VGA port
			    * One - S-Video
			    * One - IEEE 1394 (4-pin)
			    * Microphone jack
			    * Headphone jack
			    * RJ-45 port
			    * RJ-11 port
			    * Power input

Pointing device 	Touchpad with vertical scroll zone
			Device Manager info: VISTA - Synaptics ver 9.1.3.0 17 Nov 06

PCMCIA 			1 - Type I or Type II; Card Bus

Battery 		6-cell Lithium-ion

Dimensions 		1.31 to 1.40-inches (H) × 14.09-inches (W) × 10.39-inches (D)
			33 to 36 mm (H) × 330 mm (W) × 264 mm (D)

Weight 			6.40 pounds


3.  Notice the Gateway MT6840 Chipset is Intel® 945GM.
    Here are the steps I used to find the Intel SATA Drivers for my Gateway MT6840 Laptop.

    Boot a Ubuntu 7.10 LiveCD on the MT6840.  Open a terminal window.

    Type the following command
    lspci &#8211;v | less

    Now, use the spacebar to page down through the long listing to locate the most likely LAN device listing.  The Specifications
    cut sheet showed my NETWORK device as an INTEL PRO/Wireless 3945 802.11a/b/g.  In fact it showed up as a INTEL PRO/Wireless
    3945ABG in the listing.  I downloaded the &#8220;Intel® Matrix Storage Manager&#8221; file from the following Intel site.

    [http://www.intel.com/support/product.htm?iid=CorporateV3+Header_2_Support_Product](http://www.intel.com/support/product.htm?iid=CorporateV3+Header_2_Support_Product)
    [http://www.intel.com/support/chipsets/sb/CS-022034.htm](http://www.intel.com/support/chipsets/sb/CS-022034.htm)

    Notice that there are two Drivers available.  GRAPHICS DRIVER, MASS STORAGE DRIVER, and a Chipset Software Installation Utility.
    Download all these available files, and save for future needs.

    Download the Floppy Version SATA drivers to create a floppy.  Version 7.8.0.1012 - 11/9/2007

    The first thing that has to be done is to make the SATA Drivers Available either by creating a Floppy Disk
    of the Drivers, or by slipstreaming them onto the XP Install CD, or using TEXTMODE Install.

	A. USB Floppy Drive/Floppy Disk Method:

	   1) Run the SATA drivers program and build a SATA driver floppy disk
   	   1a) Attach a USB floppy to the laptop
 	   2) Put the XP installer disk in the CD driver
	   3) Hit F10 while the machine boots, choose to boot from CD
	   4) While XP fires up, hit F6 when asked
	   5) Select the Mobile SATA driver
	   6) Delete and reformat both partitions, when asked
	   7) Install XP to the new, clean partition
	   8) After XP is fully installed, install the remaining drivers.

	B. Slipstreaming SATA Drivers onto the XP Install CD Sites:
	   Ref Document: [http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation](http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation)
           [http://www.tacktech.com/display.cfm?ttid=411](http://www.tacktech.com/display.cfm?ttid=411)

	C. Another method of textmode install:
           [http://www.intel.com/support/chipsets/imst/sb/CS-020825.htm](http://www.intel.com/support/chipsets/imst/sb/CS-020825.htm)
           [http://www.intel.com/support/chipsets/imsm/sb/CS-021701.htm](http://www.intel.com/support/chipsets/imsm/sb/CS-021701.htm)
           [http://www.msfn.org/board/index.php?showtopic=13173](http://www.msfn.org/board/index.php?showtopic=13173)


4.  [http://www.msfn.org/board/index.php?showtopic=77999&st=40&p=689829&#entry689829](http://www.msfn.org/board/index.php?showtopic=77999&st=40&p=689829&#entry689829)

    Now you should have the proper drivers for:
    Video -Intel Site
    SATA Hard Drive - Intel Site
    Gateway Media Reader - Gateway Site
    LAN - Marvell Yukon 88E8038 PCI-E LAN
    [http://www.marvell.com/drivers/driverDisplay.do?dId=175&pId=6](http://www.marvell.com/drivers/driverDisplay.do?dId=175&pId=6)
    Gateway_Wireless - 3945ABG - Gateway Site

    Still need:
    Modem - Motorola SM56 Drivers
    [http://www.motorola.com/softmodem/public_d...6.12.07_DFV.zip](http://www.motorola.com/softmodem/public_d...6.12.07_DFV.zip)
    Synaptics TouchPad - (Vista - Synaptics ver 9.1.3.0 17 Nov 06) XP should have drivers included.

5.  Insert XP SP2 CD and Install XP.  Make a 60 Gig Partition for XP SP2.
    (Windows Partition = SDA1 = 60001 of 152626)
    Remaining space will be for Ubuntu 7.10.

6.  Insert Ubuntu LIVECD and Boot it.  Run Gnome Partition Editor.

    Make three partitions:  (Don't remove or work with the Windows XP Partition = SDA1)

    /		20 Gig
    /home	Remaining Space
    /swap	8 Gig

7.  Install Ubuntu 7.10 from LIVECD to the above Partition (/DEV/SDA2)
    Manual Partition Drive and Define/EDIT Mount Points.

                                   Gnome Partition Settings    Mount Point

    /DEV/SDA1  NTFS        58.59   60001                       /mnt/windows
    /DEV/SDA2  EXT3        19.53   20000                       /
    /DEV/SDA4  EXT3        70.91   Rest of Drive               /home
    /DEV/SDA5  Linux-swap   7.84   8                           /swap
    
    user =  xxx
    password =  yyy

8.  Create additional users with passwords & add more Workareas (desktops).
    Make links for all USERS to:
    COMPUTER
    TERMINAL
    CD/DVD CREATOR

9.  Connect to Internet and update Ubuntu.

10. Install other Ubuntu Software as needed:
    PSI - REF: Setup_PSI.doc
    Gparted - Gnome Partiton Editor
    Typing, Games etc.
    MP3 Player - Amarok - Copy MP3's to Music Folder

11. Use SUPER GRUB as needed to Repair Win XP or Ubuntu so they boot properly.

WIN XP SP2 NEEDS to have more DRIVERS UPDATED, and then verify that there are no YELLOW QUESTION MARKS in DEVICE MANAGER.
Be sure to RUN infinst_autol.exe. (Double Click on "infinst_autol.exe" to get rid of the SM Error in Device Manager) 

12. Finish Copying and installing Drivers for XP SP2 to update the remaining items.


Ubuntu 7.10 Installs and worked perfect.  Wireless even came up working after turning it on with FN F2.  And XP SP2 sure beats Vista!
If you're looking for a Dual Boot machine the Gateway MT6840 is hard to beat, and the price is right.

LK

---

### Post by ajmorris on 2007-12-28
Great tutorial there,
Im not quite sure that it belongs in absolute beginner talk though, could a mod please move it?

---

### Post by 63supercobrajet on 2008-01-09
Hi,
 I bought this "refurbished" MT6840 Laptop from TigerDirect for $499; -I couldn't resist, anyway so far so good Windows Vi$a Premium is a dawg, -'cause its just a "dawg". In fact there was no serial number on my laptop anywhere ?!
-Gateway are imbezels to think OpenSource is going anywhere but up and they really should start thinkin' Unix/Linux/OpenSolaris/xBSD desktop power, otherwise "GATEWAY" will end up being road-kill far behind Dell, HP/Compaq,...Sun Miocrosystems, ...
actually, they're already behind, but hey thanks for the Hardware anyway Gateway ;)
No, I'm not an Ubuntu user, I'm dual-booting WinXP/BSD/Unix only, but I don't doubt Ubuntu rocks on this little laptop.

and kudos, the "serial" number was the charm :)
thanks so much.

-a FreeUnixUser.

---

### Post by 63supercobrajet on 2008-01-09
> **ajmorris said:**
> Great tutorial there,
Im not quite sure that it belongs in absolute beginner talk though, could a mod please move it?

NOOOOO!. pleeeez don't move it, instead, just "cp/link" it to all the other pertitent formus including Hardware Compatibility lists,...there is no such thing a too much hardware info.

---

### Post by 63supercobrajet on 2008-01-09
> **63supercobrajet said:**
> Hi,
 I bought this "refurbished" MT6840 Laptop from TigerDirect for $499; -I couldn't resist, anyway so far so good Windows Vi$a Premium is a dawg, -'cause its just a "dawg". In fact there was no serial number on my laptop anywhere ?!
-Gateway are imbezels to think OpenSource is going anywhere but up and they really should start thinkin' Unix/Linux/OpenSolaris/xBSD desktop power, otherwise "GATEWAY" will end up being road-kill far behind Dell, HP/Compaq,...Sun Miocrosystems, ...
actually, they're already behind, but hey thanks for the Hardware anyway Gateway ;)
No, I'm not an Ubuntu user, I'm dual-booting WinXP/BSD/Unix only, but I don't doubt Ubuntu rocks on this little laptop.

and kudos, the "serial" number was the charm :)
thanks so much.

-a FreeUnixUser.

--------------------------------------------------------------------------

actually what I find pretty sad is that the "manufacturer'/distributor" is the one "filing" down the serial #'s so that "certain refurbished?"users can't download any drivers' ?!! like W.T.F. is this anyway ?

hooly crappppoly!
sad yes! funny NO.
 -you really are pathetic Mr/Mrs. Gateway
:lolflag:

---

