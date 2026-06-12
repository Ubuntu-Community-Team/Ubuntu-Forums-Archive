---
title: "My Problems Megapost"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Nigmah on 2007-06-25
[COLOR=DarkOrange][B]Ok so i wasn't getting any responses in other parts of this forums and i've gotten more help here than anywhere else so i'm going try get everything solved at once

First thing is the most annoying thing, after awhile using ubuntu normally whats starts to happen is ubuntu will lag major, i'm talking i get about 3 seconds of realtime page viewing then it freezes, or just switching from one window to another(ff or not) it lags a good amount.

I believe im using the propriety ati radeon drivers. I got them using envy.

Second i'm trying to get beryl to work on my ati radeon xpress integrated 200m graphics card i used this guide [http://ubuntuforums.org/showthread.php?t=341149&highlight=beryl+ati+200](http://ubuntuforums.org/showthread.php?t=341149&highlight=beryl+ati+200) but now whenever i try to log into a xgl session is just gives me this message saying that it cannot find /usr/local/bin/startxgl.sh i've double checked its there and i've made it twice with no luck.

Also im trying to use this guide [http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359) to get all my windows stuff to play nice on ubuntu. I get to the point in the guide where its telling you to install windows. Each time i try it get an error talking about my harddware with this technical error info 
[/B][/COLOR][COLOR=DarkOrange][B] exit: 0x00000012 (0x00000001 0x00000000 0x00000000 0x00000000)
I've tried it with two different vers of xp pro same thing. Thats with virtual box[/B][/COLOR][COLOR=DarkOrange][B].

There might be other things but we'll just see what happens after(if) i get these things fixed
[/B][/COLOR]

---

### Post by DBStevens on 2007-06-25
First lets start with this in terminal please run the following commands and post the output

cd /usr/local/bin
ls -o start*

Then please provide a list of your system specs and the output from

free 

at the point where your system "lags" .

---

### Post by Nigmah on 2007-06-25
heres the output of free
             total       used       free     shared    buffers     cached
Mem:        969688     927112      42576          0      16300     490640
-/+ buffers/cache:     420172     549516
Swap:      1638588          0    1638588

heres my system specs
Field    Value
Computer    
Computer Type    ACPI Multiprocessor PC
Operating System    Microsoft Windows XP Media Center Edition
OS Service Pack    Service Pack 2
Internet Explorer    7.0.5730.11
DirectX    4.09.00.0904 (DirectX 9.0c)
Computer Name    MyComputer
User Name    Administrator
Logon Domain    MyComputer
Date / Time    2007-06-25 / 12:20
    
Motherboard    
CPU Type    DualCore AMD Athlon 64 X2, 2000 MHz (10 x 200) 3800+
Motherboard Name    MSI RS480M2/RS482M2/RX480M2/RX482M2 (MS-7093) / MS-7184
Motherboard Chipset    ATI Radeon Xpress 200, AMD Hammer
System Memory    960 MB  (PC3200 DDR SDRAM)
BIOS Type    Award (12/13/05)
Communication Port    ECP Printer Port (LPT1)
    
Display    
Video Adapter    ATI RADEON XPRESS 200 Series  (256 MB)
Video Adapter    ATI RADEON XPRESS 200 Series  (256 MB)
3D Accelerator    ATI Radeon Xpress 200 (RS480)
Monitor    LG L204WT(Analog) [NoDB]  (1701193285)
    
Multimedia    
Audio Adapter    Realtek ALC658 @ ATI SB400 - AC'97 Audio Controller
    
Storage    
IDE Controller    ATI IDE Controller
IDE Controller    Standard Dual Channel PCI IDE Controller
Storage Controller    SCSI/RAID Host Controller
Disk Drive    Generic USB CF Reader USB Device
Disk Drive    Generic USB MS Reader USB Device
Disk Drive    Generic USB SD Reader USB Device
Disk Drive    Generic USB SM Reader USB Device
Disk Drive    Hitachi HDT725025VLAT80 USB Device  (250 GB, 7200 RPM, Ultra-ATA/133)
Disk Drive    WDC WD2500JS-60MHB1  (232 GB, IDE)
Optical Drive    HP DVD Writer 840b  (DVD+R9:8x, DVD-R9:4x, DVD+RW:16x/8x, DVD-RW:16x/6x, DVD-RAM:5x, DVD-ROM:16x, CD:48x/32x/40x DVD+RW/DVD-RW/DVD-RAM)
Optical Drive    IDE-DVD DROM6216
Optical Drive    JL5343Q VLU943A SCSI CdRom Device
SMART Hard Disks Status    OK
    
Partitions    
C: (FAT32)    178235 MB (8252 MB free)
H: (NTFS)    24756 MB (3165 MB free)
L: (NTFS)    20473 MB (7775 MB free)
N: (FAT32)    238414 MB (6236 MB free)
Total Size    451.1 GB (24.8 GB free)
    
Input    
Keyboard    HID Keyboard Device
Keyboard    Microsoft eHome MCIR 109 Keyboard
Keyboard    Microsoft eHome MCIR Keyboard
Keyboard    Microsoft eHome Remote Control Keyboard keys
Keyboard    Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
Mouse    HID-compliant mouse
Mouse    Laser Mouse
Mouse    PS/2 Compatible Mouse
    
Network    
Primary IP Address    192.168.0.102
Primary MAC Address    00-C0-A8-A9-9F-B8
Network Adapter    Atheros AR5006X Wireless Network Adapter  (192.168.0.103)
Network Adapter    Realtek RTL8139/810x Family Fast Ethernet NIC  (192.168.0.102)
Modem    Agere Systems PCI-SV92PP Soft Modem
    
Peripherals    
Printer    Microsoft XPS Document Writer
Printer    Send To OneNote 2007
FireWire Controller    VIA VT6307 Fire IIM IEEE1394 Host Controller (PHY: VIA VT6307)
Infrared Controller    eHome Infrared Receiver
Infrared Controller    Microsoft eHome Infrared Transceiver
USB1 Controller    ATI SB400 - USB Controller
USB1 Controller    ATI SB400 - USB Controller
USB2 Controller    ATI SB400 - USB 2.0 Controller
USB Device    eHome Infrared Receiver
USB Device    USB Composite Device
USB Device    USB Human Interface Device
USB Device    USB Human Interface Device
USB Device    USB Mass Storage Device
USB Device    USB Mass Storage Device
USB Device    Zune
    
DMI    
DMI BIOS Vendor    Phoenix Technologies, LTD
DMI BIOS Version    3.40
DMI System Manufacturer    HP Pavilion 061
DMI System Product    ER859AA-ABA M7334N
DMI System Version    0qn1114RE101AMETM00
DMI System Serial Number    MX955101W9 NA651
DMI System UUID    00922DEB-173B1110-9BDB81E5-F5B87E2E
DMI Motherboard Manufacturer    MSI
DMI Motherboard Product    AMETHYST-M
DMI Motherboard Version    1.0
DMI Motherboard Serial Number    
DMI Chassis Manufacturer    Hewlett-Packard
DMI Chassis Version    
DMI Chassis Serial Number    
DMI Chassis Asset Tag    
DMI Chassis Type    Desktop Case
DMI Total / Free Memory Sockets    4 / 2

---

### Post by Nigmah on 2007-06-25
[COLOR=DarkOrange]**bumping**[/COLOR]

---

### Post by DBStevens on 2007-06-25
Please run the following commands and post the output

cd /usr/local/bin
ls -o start*

This is for your beryl issue, I think I know what it is but would like to verify something first.

I'm looking into your performance issue.

If I read the system information correctly you have 1GB of memory on that machine.

I also have 1GB  of memory it looks like your mapping may be off, I haven't gone completely through the system but could you provide me with the actual model of that HP Pavillion you are runing.

There are many things that cause a performance issue of the nature you are talking about one of which is a MTRR setup error, it can leave areas of memory left noncacheable which when actually used will be very slow.   If there were no cache for the system you would likely faint watching it boot.  Then there is swap thrashing which will slow thngs down however I didn't see evidence of that.  How many windows did you have open and what were you running?

---

### Post by Nigmah on 2007-06-26
[B][COLOR=DarkOrange]I solved some of my problems myself, i simply reformatted. Now i have beryl up and runnning as well as not having the system lag(which i believe i know what the cause was, i set the swappiness to 5 from 60, following another guide to increase the speed of my system) 

Now i just have the problem of witch i gete get vbox up and running.

and incase you need the model still its an hp m7334n
[/COLOR][/B]

---

### Post by Nigmah on 2007-06-26
[COLOR=DarkOrange][B]I believe the root of my problem is caused by a bios error i get everytime i boot up it goes similairily to this
bios error:  8254 timer not connnected to  IO-APIC 

Now i've tried the trick were you appen noapic to the bootup bbut that didn't work and just causes it to freeze at the load screen.
I've also tried to look in my bios to turn off ACIP HPET support but either its not there or i can't find it.

Sop right now i'm in the process of updating my bios, which is taking 4ever.
[/B][/COLOR]

---

