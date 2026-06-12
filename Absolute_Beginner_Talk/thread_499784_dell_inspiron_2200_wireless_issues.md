---
title: "dell inspiron 2200 wireless issues"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by tennvolsmb on 2007-07-13
ok i've read other threads but i still can't figure it out... 
my wireless card is:

Dell Wireless 1370 WLAN Mini-PCI Card
Intel(R) PRO/100 VE Network Connection

as for lspci i have 

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

```

and as for sudo lshw -C network i have

 ```
 *-network:0 DISABLED    
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:3d:d0:49
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:dfdfe000-dfdfffff irq:19
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 03
       serial: 00:14:22:c3:17:e0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.106 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:dfdfd000-dfdfdfff ioport:df40-df7f irq:20
```

what do i do??:confused:

---

### Post by tennvolsmb on 2007-07-13
anyone?

---

### Post by tennvolsmb on 2007-07-13
so no one can help me?

---

### Post by tennvolsmb on 2007-07-13
ok i've read other threads but i still can't figure it out...
my wireless card is:

Dell Wireless 1370 WLAN Mini-PCI Card
Intel(R) PRO/100 VE Network Connection

as for lspci i have

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
```

and as for sudo lshw -C network i have
```

*-network:0 DISABLED    
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:3d:d0:49
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:dfdfe000-dfdfffff irq:19
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 03
       serial: 00:14:22:c3:17:e0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.106 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:dfdfd000-dfdfdfff ioport:df40-df7f irq:20
```

what should i do i have no idea??:confused:

---

### Post by tennvolsmb on 2007-07-13
ok i've read other threads but i still can't figure it out...
my wireless card is:

Dell Wireless 1370 WLAN Mini-PCI Card
Intel(R) PRO/100 VE Network Connection

as for lspci i have

```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

```
and as for sudo lshw -C network i have

```

*-network:0 DISABLED    
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:3d:d0:49
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:dfdfe000-dfdfffff irq:19
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 03
       serial: 00:14:22:c3:17:e0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.106 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:dfdfd000-dfdfdfff ioport:df40-df7f irq:20
```

what should i do i have no idea??:confused:

---

### Post by angryfirelord on 2007-07-13
In order for someone ot solve the problem, they need to know what the problem is. :)

Can you connect to a wireless router? What have you done so far and what were you doing when the problem occurred?

---

### Post by tennvolsmb on 2007-07-13
well i can connect to a modem using ethernet cable but i do not know how to configure my wireless help... plus linux does not pick up on any of my wireless routers i have

---

### Post by stchman on 2007-07-13
> **tennvolsmb said:**
> ok i've read other threads but i still can't figure it out...
my wireless card is:

Dell Wireless 1370 WLAN Mini-PCI Card
Intel(R) PRO/100 VE Network Connection

as for lspci i have

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
```

and as for sudo lshw -C network i have
```

*-network:0 DISABLED    
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:3d:d0:49
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:dfdfe000-dfdfffff irq:19
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 03
       serial: 00:14:22:c3:17:e0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.106 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:dfdfd000-dfdfdfff ioport:df40-df7f irq:20
```

what should i do i have no idea??:confused:

Your wireless card is a Broadcom 43xx series.  You are going to have to use the Ndiswrapper to get that one working.  As of right now Broadcom has not released drivers for Linux for their wireless cards.  You need to use the windows drivers.

Follow this procedure:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)

This should work.

---

### Post by tennvolsmb on 2007-07-13
could you tell me what to click on there is a lot to read and well i dont have that much time

---

### Post by linuxwizard on 2007-07-13
According to this Dell insprion 2200
[https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron2200](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron2200)         look at the very bottom Notes #3 shows this
[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

### Post by anewguy on 2007-07-13
I'm new to Linux and Ubuntu and have it running on a cheap Gateway laptop.  I noticed in the output of your lspci that it lists your wireless as Broadcom 4318 Air Force One.  I have that same wireless adapter in my PC.  While I can't go into all of the details (I honestly don't remember all of them), these are the main things you need:

- first, find the Windows drivers for your wireless card.  They may be available as a download from Dell's site.  You want the .inf and .sys files; in my case that was bcmwl5a.inf and bcmwl5.sys.  Copy these files to  your desktop.

- via synaptic package manager, install ndiswrapper and network-manager-gnome.  I was told that network-manager-gnome was included in my default install, but it wasn't marked in synaptic so I checked and installed it.

- sudo gedit /etc/modprobe.d/blacklist  and at the end of it add:

# no firmware, using ndiswrapper for bcm4318
blacklist bm43xx

and then save it.

- reboot your computer

- via a terminal window:
     - sudo ndiswrapper -l    <-- that's a lower case "L"
      This should say that nothing is installed.
    - sudo ndiswrapper -i ~/Desktop/bcmwl5a.inf  <-- assuming this is the name of the .sys file
    - sudo ndiswrapper -l   <-- that's a lower case "L"

  It should show your device as installed and working.  If not, try removing the listed driver via 
  sudo ndiswrapper -r xxxxxxx  <-- the "xxxxxxx" being the name of the driver without the .sys, then reinstall the driver being sure you typed the path and name correctly (I screwed this up a few times myself:)).

    - sudo depmod -a
    - sudo modprobe ndiswrapper

Now you should be able to click on the network icon on the top bar and see your wireless network.  Click it to connect.  If it needs a WEP, etc., password, it will ask and also set up a keyring for you so you don't have to keep remembering the password.

You may want to check the Ubuntu forums for more instructions, as I'm not sure if this puts ndiswrapper in for start up when you reboot or not.

Hopefully this will help you.   If not, be sure to check the ndiswrapper stuff, as it's the only way I know to get the Broadcom 4318 working reliably.

:)ooops

---

### Post by SnowflakeRV7 on 2008-01-03
> **tennvolsmb said:**
> could you tell me what to click on there is a lot to read and well i dont have that much time
I'm amazed that you think you'll get help with this kind of response.  Linux does still require some down-n-dirty command-line manipulations on systems that use hardware from closed-source vendors.  If you "don't have that much time", then Ubuntu isn't for you, at least not on the hardware you've got.  "Please somebody fix this for me because i'm too lazy to do it myself" is what it sounds like.

If you want a one-click solution because you're "too important" to take the time to learn how things work, click [here](http://www.microsoft.com).  There's a program there called Vista, it should solve all your problems and be just idiot-proof enough that you might get by.

---

### Post by kevin11951 on 2008-01-03
> **SnowflakeRV7 said:**
> I'm amazed that you think you'll get help with this kind of response.  Linux does still require some down-n-dirty command-line manipulations on systems that use hardware from closed-source vendors.  If you "don't have that much time", then Ubuntu isn't for you, at least not on the hardware you've got.  "Please somebody fix this for me because i'm too lazy to do it myself" is what it sounds like.

If you want a one-click solution because you're "too important" to take the time to learn how things work, click [here](http://www.microsoft.com).  There's a program there called Vista, it should solve all your problems and be just idiot-proof enough that you might get by.

hey! calm down! were friends here, and just trying to help each other out! anyway as for the OP's problem, i have the same card, and if you can connect to the internet at all... then there should be a popup of a restricted driver (its called bcm43xx-fwcutter) 

or if it doesn't popup, install it directly

try 

```
sudo apt-get install bcm43xx-fwcutter
```
in the terminal, it will ask a few questions, post something you dont understand here.

---

