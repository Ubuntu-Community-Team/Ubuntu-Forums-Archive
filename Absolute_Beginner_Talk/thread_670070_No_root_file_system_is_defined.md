---
title: "No root file system is defined??"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by AZGUNS on 2008-01-17
I am getting an error that says "No root file system is defined"
I have never used anyother OS other then windows I know windows 95 to windows Vista in side and out. I have my A+ cert I code in VB6 and ASM but I can not use ubuntu lol 
this is my set up
/dev/sda
/dev/sda1   ntfs   /media/sda1  76892 MB (XP Pro)
/dev/sda2   ext3  /media/sda2  13859 MB (for Ubuntu)
/dev/sda3   ntfs   /media/sda3  69281 MB (Vista)

Now I read everything I just don't get it
```
 
install thing 
https://help.ubuntu.com/community/GraphicalInstall
Posts like this one 
http://ubuntuforums.org/showthread.php?t=515770
http://ubuntuforums.org/showthread.php?t=636274
http://ubuntuforums.org/showthread.php?t=449116
http://ubuntuforums.org/showthread.php?t=222526
http://ubuntuforums.org/showthread.php?t=76322 
```

Please keep in mind I know Windows nothing else

---

### Post by kpkeerthi on 2008-01-17
Are you getting this message while installing ubuntu? Or have you installed it already?

---

### Post by camnor on 2008-01-17
Is it showing up when you go to run the partitioner when you are installing? because what you have to do is select the partition that you want to use as the linux partition, double click the mount point and when it opens up the dialog that asks you waht you want to do with it, you have to type in simply "/" and it should work just fine.  Also it will ask you to format the partition, so just tick the check box and thats it.  Other than that instance.... I can't think of why or when it would be saying that. Best of luck! Hope this helped:KS

---

### Post by AZGUNS on 2008-01-17
Im trying to in stall it now it's ubuntu 7.10. You see Like I said I only know windoes and I want to get away from there crap Vista sucks so bad 10,000 pop ups just to tell me the internet can give me a virus and well it sucks everyone know it sucks lets face it. Anyway sorry lol So I tryed reading some stuff about /dev and people with same error but there talking greek to me. I'm sure its really easy I just don't know how to set my drive up right I mean it's a triple boot set up 
"keep in mind I can and will reformat the drive and start again"
 cause its a new laptop.

Came with Vista. Has new SATA hard drive on it so I had to splitstream XP to get it on the drive in the frist place. So now I got Vista and Xp dual-boot all set up. So now I want to set ubuntu up for a triple boot cause I would like to learn how to use it

I'm in stalling to a laptop heres all the info you could ever need
```


General 
Platform Technology Intel Centrino Duo  
System Type Notebook  
Built-in Devices Wireless LAN antenna  
Width 13 in  
Depth 10.4 in  
Height 1.4 in  
Weight 6.2 lbs  
Notebook type Mid-size laptops (6-7.5 lbs.)  
Screen type Wide-screen  
Wireless Capabilities 802.11b, 802.11g, 802.11a  
Processor 
Processor Intel Core 2 Duo T5300 / 1.73 GHz  
Multi-Core processor technology Dual-Core  
64-bit processor Yes  
Data bus speed 533 MHz  
Chipset type Mobile Intel 945GM Express  
Cache Memory 
Type L2 cache  
Cache size 2 MB  
RAM 
Installed Size 2 GB  
Technology DDR II SDRAM - 533 MHz  
RAM form factor SO DIMM 200-pin  
RAM configuration features 2 x 1 GB  
Storage Controller 
Storage controller type Serial ATA  
Storage Controller / Serial ATA Interface Serial ATA-150  
Storage 
Floppy Drive None  
Hard Drive 160 GB - Serial ATA-150 - 5400 rpm  
Storage Removable None  
Hard drive type Portable  
Optical Storage 
Type DVD±RW (±R DL) - Integrated  
CD / DVD read speed 24x (CD) / 8x (DVD)  
CD / DVD write speed 24x (CD) / 8x (DVD±R) / 2x (DVD-R DL) / 2.4x (DVD+R DL)  
CD / DVD rewrite speed 16x (CD) / 8x (DVD)  
Optical Storage (2nd) 
2nd optical storage type None  
Card Reader 
Card reader type 4 in 1 card reader  
Supported flash memory cards Memory Stick, MultiMediaCard, SD Memory Card, Memory Stick Pro  
Display 
Display Type 15.4 in TFT active matrix  
Max Resolution 1280 x 800 ( WXGA )  
Widescreen Display Yes  
 Video 
Graphics Processor / Vendor Intel GMA 950  
Video Memory Dynamic Video Memory Technology 3.0  
Max allocated RAM size 224 MB  
Audio 
Audio output type Sound card  
Audio output compliant standards High Definition Audio  
Audio Input None  
Input Device(s) 
Input device type Keyboard, Touchpad  
Telecom 
Modem Fax / modem  
Max transfer rate 56 Kbps  
Protocols & Specifications ITU V.92  
Networking 
Networking Network adapter  
Networking / Wireless LAN Supported Yes  
Wireless NIC Intel PRO/Wireless 3945ABG  
Data link protocol Ethernet, IEEE 802.11a, IEEE 802.11b, IEEE 802.11g, Fast Ethernet  
Networking standards IEEE 802.11a, IEEE 802.11b, IEEE 802.11g  
Expansion / Connectivity 
Expansion Bays None  
Expansion Slots Total (Free) 2 ( 0 ) x Memory - SO DIMM 200-pin, 1 ( 1 ) x CardBus - Type I/II  
Interfaces 4 x Hi-Speed USB - 4 pin USB Type A, 1 x Display / video - VGA - 15 pin HD D-Sub (HD-15), 1 x Display / video - S-video output, 1 x IEEE 1394 (FireWire) - 4 pin FireWire, 1 x Microphone - Input - Mini-phone 3.5 mm, 1 x Headphones - Output - Mini-phone stereo 3.5 mm, 1 x Modem - Phone line - RJ-11, 1 x Network - Ethernet 10Base-T/100Base-TX - RJ-45  
Power 
Power device form factor External  
Voltage Required AC 120/230 V  
Battery 
Technology 8-cell Lithium ion  
Installed Qty 1  
Operating System / Software 
OS Provided Microsoft Windows Vista, Microsoft Windows Vista Home Premium  
Software type Adobe Reader, Google Toolbar, CyberLink Power2Go, Microsoft Works 8.5, Microsoft Money 2006, Microsoft Internet Explorer 7.0, McAfee Internet Security Suite (90 days subscription), Microsoft Office 2007 Home and Student Edition (Trial)  
Manufacturer Warranty 
Service & support type 1 year warranty  
Service & Support Details Limited warranty - Parts and labor - 1 year  
 
```

---

### Post by insane_alien on 2008-01-17
you have selected to mount ubuntu's partiotion on /media/sda2 this is wrong.

it should be mounted on '/' which is the root filesystem. without a / there can be no /media/sda2.

you might also want to think about throwing a swap partition in there as well.

---

### Post by jonnywombat on 2008-01-17
Are you installing from the live cd?

I would try this..

During the install process when you get to the partitioning options select to manually edit partitions..
Delete your ext3 partition so you now only have free space.
Then go back a step, and this time instead of selecting manually partition select install in largest free space options..
Let this installation process run and when grub sets up make sure it detects all the other os you have installed.. After a restart you should be good to go.

---

### Post by AZGUNS on 2008-01-17
how would I set up the swap partition? and do I need this with 2g of ram? also I wanted to say thanks to you guys for the help

---

### Post by Sef on 2008-01-17
> how would I set up the swap partition? and do I need this with 2g of ram? also I wanted to say thanks to you guys for the help

Unless you are doing some heavy gaming, or movie editing, or something else that is really ram intensive, you really don't need to set up a swap partition.  However, if you do, then just make it for 1 gigabyte.

To make a swap partition, when you are partitioning, under 'Use As'.

---

### Post by louieb on 2008-01-17
> **AZGUNS said:**
> ...
/dev/sda1   ntfs   /media/sda1  76892 MB (XP Pro)
/dev/sda2   ext3  /media/sda2  13859 MB (for Ubuntu)
/dev/sda3   ntfs   /media/sda3  69281 MB (Vista)
...
Do you need swap? - only if you plan to hibernate the compter.
Open up your partition editor. on the the live CD theres one under System>Administration.
Delete sda2 and use the now unallocated space to create an extended partition.
Create 2 logical partitions within the extended partition one for root / and one for swap. They will be sda5 and sda6.

Reboot and start the install. When you get to partitioning choose manual. right click on (i think) on sda5 chose edit and set its mount point to / (root). do the same for sda6 and mount it as swap.

You should be good to go on with the install now.
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")
[Psychocats Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php")

---

### Post by AZGUNS on 2008-01-18
Thanks guys this really helped me out

---

