---
title: "Brand new to Ubuntu and can't figure out Wireless"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Demodocus on 2008-04-13
Hi all,

As the title suggests, I just installed Ubuntu for the first time on a spare desktop I had sitting around.  Everything went smoothly except for the fact that I cannot access the internet through my wireless card.  I tried some of the basic troubleshooting and from what I can see, it says that the wireless card is actually disabled (although it is recognized in device manager.)  I can't seem to find any way to enable the card however.  Anyone know how I can go about doing this?  Thanks in advance.

---

### Post by russo.mic on 2008-04-13
What kind of wireless card do you have?  Broadcom or Atheros?  This makes a difference.  

NDISWrapper is my poison of choice.

Plenty of howtos here in the forums for that.  You could also compile MadWIFI if you've got an Atheros card.  

Russo

---

### Post by 1/0 on 2008-04-13
Any WIFI button thats not enabled (as in a button on the laptop not inside *buntu)? What card is it?

```
lspci |grep net
```

---

### Post by Demodocus on 2008-04-13
The card is a Linksys (which i believe is Broadcom) WMP54GS.  From what I can tell, unless I'm misunderstanding what I'm seeing, it is recognized by Ubuntu, it just says that is is not enabled.  Do I need to get the windows driver and do that NDIS wrapper thingy?  Oh, and it's in a desktop I built myself, no laptop involved.  I previously had Win XP installed on the comp and all I did was switch in a different hard drive I had to install Ubuntu on.

---

### Post by hyper_ch on 2008-04-13
well, we need to know the chipset... paste the output of the code given above

---

### Post by Demodocus on 2008-04-13
00:08.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

So it appears to be seeing the regular ethernet card I have installed instead of the wireless when I ran that lspsci command.

---

### Post by hyper_ch on 2008-04-13
pls paste

```

lspci

```

and 

```

lsusb

```

---

### Post by Demodocus on 2008-04-13
from lspci:
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:06.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:06.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:06.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
00:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:08.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 GS] (rev a1)

from lsusb:
Bus 007 Device 004: ID 1b1c:1a90  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by hyper_ch on 2008-04-13
broadcom chip.... no clue but often you need to use ndiswrapper to get that running

---

### Post by Demodocus on 2008-04-13
All right, so do I have to delete what is there already?  And then just do the wrapper with the windows driver that is available?  Or can i just do the wrapper without deleting anything?

---

### Post by 1/0 on 2008-04-13
One of these should do the trick:

[http://ubuntuforums.org/showthread.php?t=424994](http://ubuntuforums.org/showthread.php?t=424994)

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D)

[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

---

### Post by Demodocus on 2008-04-13
Thanks for all the quick and helpful responses, I'll try these out when I get home tonight and let you know how everything goes!

---

### Post by thorgal on 2008-04-13
it's a chip supported by the kernel driver 'b43'.
You need the broadcom firmware though.

Which linux kernel do you have ?

do the following in a terminal and report screen outputs here :

```
uname -r
```
reports the kernel version

```
sudo apt-get install b43-fwcutter
```
this will install the broadcom firmware to work with the broadcom driver b43

```
lsmod | grep b43
```
reports if b43 is already loaded. If loaded, type 

```
sudo rmmod b43
dmesg | tail -n 10
``` 
You unload the b43 module from the kernel space and check that the system did so properly)

```
ls /lib/firmware
```
check that you have the b43 firmware installed correctly

```
sudo modprobe b43
dmesg | tail -n 50
```
you reload the b43 kernel module and check that the system did just that with proper initialization of your card thanks to the firmware being loaded.

At the same time, the dmesg will spit out which network interface name the udev  system has given to it, something like eth0, eth1, wlan0, wlan1, it can be different but you will find the name easily. Note that you can make your own interface name by editing udev rules but that's really not for the newbies!

OK, now you have to configure this interface with your wireless network configuration. That's something you can do easily with the network conf applet provided by your windows manager (gnome or kde I presume). In kde, it's called something like network-manager-kde and in gnome, it's (surprise surprise) network-manager-gnome :)

I hope this is not too geekish! I own a PCMCIA card using the same chipset running from my Kubuntu laptop (the miniPCI card died and I did not want to replace it since I already had that PCMCIA card lying around). The b43 kernel driver works really nicely. They came a long way to get a useful driver for broadcom (used to be called bcm43xx and it did suck a bit but that's history now).

---

