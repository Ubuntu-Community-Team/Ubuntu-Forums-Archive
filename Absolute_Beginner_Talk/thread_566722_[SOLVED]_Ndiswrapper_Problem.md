---
title: "[SOLVED] Ndiswrapper Problem"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by rlj999 on 2007-10-03
Toshiba Lap

My Wireless connection shows  connection activity  but not able to connect with internet -- so 

installed Nrapper - blacklisted existing drivers -(now show none) downloaded driver from Intel  that corresponds to my need (Intel Pro Wireless 2200BG) as there are a number of sys. files do I copy all of those to driver folder? 

Have read that often one has to try a number of the drivers if one does not work  Any advice ?

Thanks 

Robert

---

### Post by tdrusk on 2007-10-03
Don't worry about that just yet. I will try to find you a guide for your wireless.

Open a terminal and put in
```
lspci
```
and press enter. 

Copy that output and paste it here. That will help us a ton.

---

### Post by bobplano on 2007-10-03
yes once you get the drivers you copy the .sys files to /etc/ndiswrapper/*folder_name*

you can install the drivers with sudo ndiswrapper -i *driver.inf*

i've never had to try different drivers; just make sure the ones you have are for your card

---

### Post by rlj999 on 2007-10-04
> **fuzzyhair said:**
> Don't worry about that just yet. I will try to find you a guide for your wireless.

Open a terminal and put in
```
lspci
```
and press enter. 

Copy that output and paste it here. That will help us a ton.

lj999@rlj999-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
07:00.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
07:00.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
rlj999@rlj999-laptop:~$ 

Hope this will help -- still struggling with this 

Thnks

---

### Post by tdrusk on 2007-10-04
> **rlj999 said:**
> lj999@rlj999-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
07:00.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
07:00.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
rlj999@rlj999-laptop:~$ 

Hope this will help -- still struggling with this 

Thnks

Try this.
[http://ubuntuforums.org/showthread.php?t=13576&highlight=Intel+2200BG](http://ubuntuforums.org/showthread.php?t=13576&highlight=Intel+2200BG)

---

### Post by Lambert on 2007-10-04
> **fuzzyhair said:**
> Try this.
[http://ubuntuforums.org/showthread.php?t=13576&highlight=Intel+2200BG](http://ubuntuforums.org/showthread.php?t=13576&highlight=Intel+2200BG)

You went way back to early 2005 on that guide. That's not necessary as the driver is already installed in recent versions.

The question to OP is what lead you to drop the native driver and go with ndiswrapper? What version of ubuntu do you have installed? 

Not sure how much troubleshooting was done but the intel 2200 driver has good support in ubuntu so it might have been something minor.

---

### Post by rlj999 on 2007-10-04
I dropped the native driver because although it showed connectivity but no real results in attempting to connect ..

I suppose I could move back to the original driver but am not sure how that is done 

Meanwhile here is what I have done so far 

Have arrived at this step on wireless install for Toshiba  driver  Intel Pro wireless 2000BG  Ubuntu 6-10
Downloaded the driver , installed Ndiswrapper – black listed other drivers  (following which my wireless panel no longer was displayed)  followed instructions in book but have not been able to move ahead  

See terminal entries below 

rlj999@rlj999-laptop:~$ cd /home/rlj999/Desktop/Driver
rlj999@rlj999-laptop:~/Desktop/Driver$ sudo ndiswrapper -i w29n51.inf
w29n51 is already installed. Use -e to remove it
rlj999@rlj999-laptop:~/Desktop/Driver$ sudo ndiswrapper -m
modprobe config already contains alias directive

rlj999@rlj999-laptop:~/Desktop/Driver$ gksu gedit /etc/modules

(gedit:7023): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
 
After entering ndiswrapper the  following screen appeared 

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
ndiswrapper
ndiswrapper
ndiswrapper


Robert   rlj999

---

### Post by rlj999 on 2007-10-05
Having problems with Ndiswrapper -- and would like to reinstall the blacklisted drivers -- but am not sure how that is done --
please advise 

thnks

---

### Post by Achetar on 2007-10-05
I am having the EXACT same problem as you rlj999, Except my Wi-Fi card is the infamous Linksys WPC54G v3 card. I have the Linksys Driver installed using ndiswrapper. It used to be connecting fine. Now it rarely connects. What is the deal? (PS i think a kernel update may have done it)

---

### Post by rlj999 on 2007-10-05
My card is internal  -- and although it seems that I downloded the driver for the card to enter it comes up as being an invalid driver -- I'm a bit cofused as to what Sys. and inf files I should enter as there are a number listed on the driver file.

Any ideas ?

Robert

---

### Post by Lambert on 2007-10-05
> **rlj999 said:**
> Having problems with Ndiswrapper -- and would like to reinstall the blacklisted drivers -- but am not sure how that is done --
please advise 

thnks

First take the interface down

```

sudo ifdown wlan0

```

Next unload the ndiswrapper module

```

sudo modprobe -r ndiswrapper

```

Next you need to uninstall ndiswrapper depending on what version and how you installed. Through synaptic it's easy, if you built from source code a newer version then you will have to go back to the source folder and do a make uninstall (I believe that's correct, someone correct if I'm missing something)

Open the blacklist file and remove the line with the driver on it and save the file.

Reboot and come back here and post the output of this command

```

sudo lshw -C network

```

You can also try to connect at this point and post results.

---

### Post by rlj999 on 2007-10-05
Thanks 

Heading into Manhattan --evening event will regroup later this evening will report later  
Have printed out instructions 
Robert

---

### Post by rlj999 on 2007-10-06
Lambert 

Followed he instructions sent --- Wireless option appeared and  my connection   showed up on top
bar as being connected 
reading Connection Properties  eth0
signal strength  93%

at that time I downloaded some files to update system etc (balloon appeared asking me to down load) all the files were downloaded successfully  -- but when I attempted to go on line using Firefox the “could not find server' message appeared – could the problem be somehow related to the browser?

Feels like I am getting closer !

Again thnks 
Trust that someone will come up with an answer!

rlj999@rlj999   

rlj999@rlj999-laptop:~$ gksu gedit /etc/modprobe.d/blacklist
(gedit:5103): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
rlj999@rlj999-laptop:~$ 

rlj999@rlj999-laptop:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1
       version: 10
       serial: 00:0f:b0:9a:85:9d
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sky2 driverversion=1.6.1 firmware=N/A link=no multicast=yes port=twisted pair
       resources: iomemory:b4000000-b4003fff ioport:3000-30ff irq:233
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@06:02.0
       logical name: eth0
       version: 05
       serial: 00:13:ce:37:f6:11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.1.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:b8006000-b8006fff irq:50
  *-usb
       description: Bluetooth wireless interface
       product: Bluetooth Dongle (HCI mode)
       vendor: Cambridge Silicon Radio, Ltd
       physical id: 1
       bus info: usb@6:1
       version: 19.58
       capabilities: bluetooth usb-2.00
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
rlj999@rlj999-laptop:~$

---

### Post by rlj999 on 2007-10-06
Latest info 

When Wireless Connection is enabled my connection icons show a valid connection but a  message is shown "no connection to site " check spelling etc --  not sure of how I view the proxy settings -- under windows I have running " no proxies)  

Need advise on next step -- earlier messages give status info on all drivers etc 

rlj999

---

### Post by rlj999 on 2007-10-07
It appears I have made a mistake -- when looking at my connection box I mistakenly chose lo over eth0 and lost my wireless connection  checking I found that it appears i disabled all network connections -- need help  on restoring my  network connections 
and still looking for help on original problems of not reaching internet via wireless 

rlj999

---

### Post by rlj999 on 2007-10-07
Still in trouble and looking for help on restoring my network connections 

When  opening  my connection symbol  I receive the  following error message 

SIOCGIFFLAGS error  no such device 

See below to see start of latest problem

> **rlj999 said:**
> It appears I have made a mistake -- when looking at my connection box I mistakenly chose lo over eth0 and lost my wireless connection  checking I found that it appears i disabled all network connections -- need help  on restoring my  network connections 
and still looking for help on original problems of not reaching internet via wireless 

rlj999

---

### Post by rlj999 on 2007-10-08
Re installed with 7.4 which solved all the problems -- network ok 

many thanks to all

---

