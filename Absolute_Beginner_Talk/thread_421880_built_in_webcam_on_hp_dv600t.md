---
title: "built in webcam on hp dv600t"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-04-24
I have a built in webcam on my hp dv600t nothing will ever detect it, how can i fix this

---

### Post by Kobalt on 2007-04-24
First we need to know the exact model  of your webcam. Can you post the output of the following command line : ```
lspci
lsusb
```

---

### Post by mojo123 on 2007-04-24
alan@alan-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
05:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by Kobalt on 2007-04-24
And how about *lsusb* ?

---

### Post by mojo123 on 2007-04-24
Bus 005 Device 002: ID 05ca:1870 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

---

### Post by Kobalt on 2007-04-24
All right then, it's there : **Bus 005 Device 002: ID 05ca:1870 Ricoh Co**., Ltd. You can get it working this way.
Download this archive and extract it to your home folder : [http://ubunteros.free.fr/r5u870-0.10.0.tgz](http://ubunteros.free.fr/r5u870-0.10.0.tgz)
Open up a Terminal and enter these command lines : 
```
sudo mv r5u870-0.10.0 /opt
cd /opt/r5u870-0.10.0
sudo make
sudo make install
sudo modprobe r5u870
```
This will install the brand new drivers for your webcam. You can test it in Ekiga or aMSN...

---

### Post by mojo123 on 2007-04-24
the webcam is detected but i am having errors like in camorama it sais could not connect to video device? how can i fix this? The blue LED is lit so thaat means that my webcam is in use but all i see is a black screen on my webcam sessions

---

### Post by Atomic Dog on 2007-04-24
I got my package from here. [http://www.arakhne.org/spip.php?article51](http://www.arakhne.org/spip.php?article51)

  Easier to just use the deb package.

Works with .17-11 generic.

---

### Post by mojo123 on 2007-04-24
wait im a noob but thats for the dv6000t webcam?

---

### Post by mojo123 on 2007-04-24
please help

---

### Post by silverglade00 on 2007-04-24
If it's anything like my dv2000 webcam, it will only work in Ekiga or possibly aMSN. The problem is that the webcam uses Video4Linux 2 and most programs use Video4Linux 1. Ekiga uses V4L2, so it works in there. Try it in Ekiga. It should turn on and you can see yourself. Then it's just waiting for the sofware authors to start using V4L2 in Camorama and stuff.

---

### Post by chris062689 on 2007-04-24
Hey, I'm thinking about getting the same laptop, how does it run?
Do the fans run properly?  Did you have any other problems other than the web camera?

---

### Post by mojo123 on 2007-04-24
nop its just amazing the dv6000t is such a low price and so many features integrated!

---

### Post by BC7333 on 2007-07-31
> **Kobalt said:**
> All right then, it's there : **Bus 005 Device 002: ID 05ca:1870 Ricoh Co**., Ltd. You can get it working this way.
Download this archive and extract it to your home folder : [http://ubunteros.free.fr/r5u870-0.10.0.tgz](http://ubunteros.free.fr/r5u870-0.10.0.tgz)
Open up a Terminal and enter these command lines : 
```
sudo mv r5u870-0.10.0 /opt
cd /opt/r5u870-0.10.0
sudo make
sudo make install
sudo modprobe r5u870
```
This will install the brand new drivers for your webcam. You can test it in Ekiga or aMSN...

Would this work for 

Bus 005 Device 003: ID 05ca:**1803** Ricoh Co.,Ltd

??

---

### Post by kornface13 on 2007-08-15
I'm having the same problem...my laptop is just a little bit older, but it's an HP dv6000.  I did everything below but then realized I probably don't have the same webcam...

How do you know if the webcam was detected or not??

Here's the output from those files...

kornface13@DeezNuts:/$ lsusb
Bus 005 Device 005: ID 13fd:0540  
Bus 005 Device 003: ID 0c45:62c0 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c03d Logitech, Inc. 
kornface13@DeezNuts:/$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7400 (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


thanks alot in advance.

---

### Post by IceDragonkin on 2008-05-14
I'm having problems too. I'm running a DV 9000 and heres what mine says when i type lsusb

Bus 005 Device 002: ID 0c45:62c0 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000 

I hope it's an easy fix.

---

### Post by charlemagne86 on 2008-05-23
> **IceDragonkin said:**
> I'm having problems too. I'm running a DV 9000 and heres what mine says when i type lsusb

Bus 005 Device 002: ID 0c45:62c0 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000 

I hope it's an easy fix.
hey everyone...i had some problems too with my integreted webcam...so i searched oline and this is what i found out...


in the output of lsusb,

the ID, or the last part is in th eform of xxxx:yyyy zzzzzzzzzzz

where xxxx is the vendor id, yyyy is the model id and then zzzzzzz is the company name...


so al u ppl need to do is seach online for driver file....but you must take care to mention the device vendor ID and model ID to get the right drivers/tutorials..


thats for general public info!!

---

### Post by charlemagne86 on 2008-05-23
HEY EVERYONE

for all those people who have got their webcams working on ekiga but after a sec or so they begin showing distortions with funny black/red/pink/green colors.....i found a sollution:

when you start ekiga webcam, when this distortion happens....just clik on the brightness slider in the video tab (even the minutest adjustment will do) and the distortions are all gone...even after you restart ekiga again....However you have to do this after each reboot.

---

