---
title: "HP5370C scanner detected but not working"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by stig on 2006-12-18
Hello,
I'm trying to use an HP ScanJet 5370C scanner with my PC (2.8GHz, 1024MB RAM, 2x80GB hard disks) using Ubuntu 6.06. This USB scanner works perfectly on my Windows PC. I should add that it is switched on, connected to the USB port and not locked.

I have sane and xsane installed and I've read various web pages and guides but still cannot get it to scan. When I launch xsane from the menu or launch sane with xscanimage I get the software. I then click on scan or preview but my scanner buzzes for a second and then nothing happens for a few minutes and the software is greyed out. Sometimes the scanner lamp flashes on and off repeatedly, three flashes at a time. Then I get an error message saying "Failed to start scanner. Error during device I/O".

The following site tells me the HP 5370C is an Avision OEM scanner labelled by HP:
[http://www.exactcode.de/oss/avision/index.html](http://www.exactcode.de/oss/avision/index.html) 
Under a listing of devices, the web site has the 5370C as working with sane: 
"ScanJet 5370C (USB, good, USB ID: 0x03f0,0x0701, 1 pass, 2400 dpi - some FW revisions have x-axis image scaling problems over 1200 dpi)"

It also says "SANE/Avision is included in the official SANE distribution for years now. So a version of the backend should already be installed with your Linux distribution." Therefore I should have the backend installed.

When I do:
$ cat /proc/bus/usb/devices
I get the following entry:

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=03f0 ProdID=0701 Rev= 0.01
S:  Manufacturer=Hewlett Packard
S:  Product=Hewlett Packard ScanJet 5300C/5370C
S:  SerialNumber=TW08J21347VE
C:* #Ifs= 1 Cfg#= 1 Atr=40 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=00(>ifc ) Sub=00 Prot=00 Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS=   8 Ivl=0ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
E:  Ad=83(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms

....but  $ cat /proc/bus/usb/drivers gives:
cat: /proc/bus/usb/drivers: No such file or directory

Running $ lsusb gives:
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 03f0:0701 Hewlett-Packard ScanJet 5300c/5370c
Bus 002 Device 001: ID 0000:0000

Running $ sane-find-scanner gives [clipped]:

  # sane-find-scanner will now attempt to detect your scanner...
  # No SCSI scanners found. If you expected something different...
  found USB scanner (vendor=0x03f0 [Hewlett Packard], product=0x0701 [Hewlett Packard ScanJet 5300C/5370C ]) at libusb:002:002
  # Your USB scanner was (probably) detected. It may or may not be supported by SANE. Try scanimage -L and read the backend's manpage.
  # You may want to run this program as root to find all devices. Once you found the scanner devices, be sure to adjust access permissions as necessary.
  
 Running $ scanimage -L gives:
device `avision:libusb:002:002' is a Hewlett-Packard ScanJet 5370C flatbed scanner
but running this after a re-boot gave:
device `avision:libusb:002:003' is a Hewlett-Packard ScanJet 5370C flatbed scanner

The /etc/sane.d/hp.conf file is as follows:

scsi HP
# Uncomment the following if you have "Error during device I/O" on SCSI
#   option dumb-read
#
# The usual place for a SCSI-scanner on Linux
/dev/scanner
#
# USB-scanners supported by the hp-backend
# HP ScanJet 4100C
usb 0x03f0 0x0101
# HP ScanJet 5200C
usb 0x03f0 0x0401
# HP ScanJet 62X0C
usb 0x03f0 0x0201
# HP ScanJet 63X0C
usb 0x03f0 0x0601
#
# Uncomment the following if your scanner is connected by USB,
# but you are not using libusb
# /dev/usb/scanner0
#   option connect-device

 I've tried a number of other things from searching the Ubuntu forums and I found this thread
 [http://www.ubuntuforums.org/showthread.php?t=252759&highlight=hp+5370+scanner](http://www.ubuntuforums.org/showthread.php?t=252759&highlight=hp+5370+scanner)
 which suggests that a lot of people were having trouble with sane scanners earlier this year on shifting from Breezy to Dapper.
  
 I'm not familiar with Linux or any software in detail and would appreciate some help. The Sane/Avision web page seems to say that the 5370C should work if I have sane installed, but it doesn't and there seem to be "things missing". But I don't know what to do next. And I'm not really sure whether I should be running the software by launching xsane from the menu or launching sane with   xscanimage.

---

### Post by stig on 2006-12-18
Anyone?

---

### Post by hobo on 2007-03-03
I maybe wrong but shouldn't the 5300c be pointing to the avision.conf file. You can display this with xsane running, by ctrl-I and look at what backend is loaded. I uncommented the line in the avision.conf file that relates to ID 03f0:0701 and the line above it. My 5300c works but not a some DPIs. It will freeze at 150dpi for instance. But it is working (sorta) @ Dapper 6.06.

---

### Post by LaidbackBill on 2007-05-14
I'd be interested to know if you ever got the 5370 to work as I'm in the process of connecting mine up as the last piece of the puzzle.  I've been looking at the same page(Link)  you did thinking I might get it to work but should have known better.

Thanks; Bill

---

### Post by JAPrufrock on 2007-05-14
It could be something simple like setting adjustments in xsane.  I'm at an XP computer right now, but I believe that there are two -time- settings in XSane (something like lamp warm-up time and scanner off time, or something similar).  If these settings are very high, you will wait for a long time before the scanner starts, or if they are negative, the scanner will never start.

---

### Post by charliehagies on 2008-07-07
My HP5370C ScanJet is detected and I can choose between the 2 scanners I have on the network. I open XSane, select the HP5370C ScanJet and try to acquire the image. XSANE closes with no errors on the screen. The app just closes. I try with gscan2pdf, the usb scanner is seen. I click on Scan and get the following error 

**"Unknown message: Segmentation Fault"** 

My HP psc 2510 network scanner works perfectly so I hope that it is just a setting that needs adjusting on Ubuntu. 

I have the following hardware and software config: 

Intel Core Duo 1.8, 2gig Ram, Intel DG33BU Motherboard on Ubuntu 8.04 "Hardy" with all updates complete.

If anyone has any ideas, I would really appreciate the help to resolve this error or where to look.

Thanks!

---

### Post by ItalOz on 2008-07-10
same problem here, the 5370C works perfectly in wXP no way to see it under Ubuntu 7.10
When I start XSane the ligth turns on but the scan is not detected in any way by the software.

...so BUMP! ;-)

---

