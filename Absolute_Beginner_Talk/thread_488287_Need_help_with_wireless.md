---
title: "Need help with wireless"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-06-30
Hello,

I am running version 7.04 Ubuntu.  I Have a Belkin 802.11G wireless card.  I cannot get the OS to recognize the card mush less connect to the net.  I realize that there are a bunch of forums on wireless but i couldnt find one that was specific to my problem.  Please help.

---

### Post by deadgobby on 2007-06-30
I hate to guide you to a link, but most wireless cards can work right of the box with ubie. Yet, it seems that you have one that does not. Which sucks. Try this guide and see if you can get Ubie to grab it and go. Some times with lap tops there can be bugs with HW and wifi cards. All so if the Radio Frequency is really encrypted it will not connect. For example at my work we use RF and the truck drivers cry that they cannot get connected to it.  
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
Try the guide and see if that helps.
Gobby

---

### Post by ITdrummer on 2007-06-30
> ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 510MB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.20GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 15.2.9
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: e8000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e8000000-efffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: driver=i810_smbus latency=0
             resources: iomemory:e0000000-e7ffffff iomemory:f6f80000-f6ffffff irq:11
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:bf80-bf9f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:bf40-bf5f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:bf20-bf3f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:f6f7fc00-f6f7ffff irq:11
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@02:01.0
                logical name: eth0
                version: 01
                serial: 00:0d:56:e9:94:ee
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.1.3 latency=32 multicast=yes
                resources: iomemory:fcffe000-fcffffff irq:7
           *-pcmcia
                description: CardBus bridge
                product: PCI1510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@02:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: iomemory:fc000000-fc000fff irq:11
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:bfa0-bfaf iomemory:34000000-340003ff irq:11
           *-cdrom
                description: DVD reader
                product: CDRW/DVD SBW-242
                vendor: QSI
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: UD22
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: ioport:c800-c8ff ioport:cc40-cc7f iomemory:f6f7f800-f6f7f9ff iomemory:f6f7f400-f6f7f4ff irq:7
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=0
             resources: ioport:c400-c4ff ioport:c080-c0ff irq:7
     *-network DISABLED
          description: Wireless interface
          product: BCM4306 802.11b/g Wireless LAN Controller
          vendor: Broadcom Corporation
          physical id: 0
          bus info: pci@03:00.0
          logical name: eth1
          version: 03
          serial: 00:11:50:4f:3e:d7
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master ethernet physical wireless
          configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 multicast=yes wireless=IEEE 802.11b/g
          resources: iomemory:f8000000-f8001fff irq:11


I dont know if this would help....

---

### Post by ITdrummer on 2007-06-30
bump

---

### Post by ITdrummer on 2007-07-01
When i click on system>>Administration>>Network  It shows a wireless connections on the list.  Does this mean that the OS is recognizing my card, but the driver is not installed or enabled?

---

### Post by chamberlain2006 on 2007-07-01
If the wireless comes up on the menu, it should be working.  Try clicking on it and configuring it.

---

### Post by oilchangeguy on 2007-07-01
if it shows on the list, then the computer sees it. make sure it's enabled, properly set any security you may have. and make sure the network manager is set to wlan0. and you should be able to connect.

---

### Post by ITdrummer on 2007-07-01
how do i set the network manager?

---

### Post by oilchangeguy on 2007-07-01
> **ITdrummer said:**
> how do i set the network manager?

in 6.06 (the version i use) right click the top or bottom panel. add to panel, locate the network manager, and add it to the panel. then open it, and from the drop down menu, select wlan0.

---

### Post by ITdrummer on 2007-07-01
It shows up but i cant get in enabled.

---

### Post by ITdrummer on 2007-07-01
theres no option called wlan0

---

### Post by ugm6hr on 2007-07-01
This is important:
> product: BCM4306 802.11b/g Wireless LAN Controller

This is the one wifi chipset that is a nightmare in Linux/Ubuntu.  Search for "BCM43" or "Broadcom" in these forums for a variety of how-to's.

---

### Post by ITdrummer on 2007-07-02
Anyone else have a suggestion?

---

### Post by ITdrummer on 2007-07-02
bump

---

### Post by ugm6hr on 2007-07-02
A simple search revealed this:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)

As mentioned, I know there are other how-to's if that doesn't work.

---

### Post by Rhumbline on 2007-07-02
This is really lame but that's my level.
I had the same prob.
The wireless came up with other connections but there were no lights on the card.
It took me a while to realise that there is a little tick box which needs to0 be ticked....
I suppose you've done that.

---

### Post by ITdrummer on 2007-07-02
I was hoping thats all it was, but i cant find that "little tick box that needs to be ticked"
  The only box i come across is "enable radio" (or similar to that)  in the network manager.

It is already checked, and all other editable options in that window are greyed out (DHCP, ESSID, password)

I just find it akward that my OS is recognizing that i have a wireless card, it recognized what chipset it uses, but not even the power light on the card blinks.. This wireless networking in linux sucks! 

Nevertheless, i shall perservere!

---

### Post by ITdrummer on 2007-07-02
> **Rhumbline said:**
> .
It took me a while to realise that there is a little tick box which needs to0 be ticked....
I suppose you've done that.

Which tick box are you referring to?

---

### Post by Rhumbline on 2007-07-02
In my 'Networking' there is an insignificant little box right next to the wireless icon and all I had to do was to click on it and a tick appeared. Otherwise it shows a dash (-).

---

### Post by ITdrummer on 2007-07-02
And after you did that, your lights started blinking and your network card was working correctly....?

I hope mine is that simple, but seeing as how I have had nothing but trouble since day 1, i doubt it!

---

### Post by Rhumbline on 2007-07-02
Crazy but true...it was that simple.

---

### Post by ITdrummer on 2007-07-02
When i get home from work (~5:30) i will post screenshots of various things i am seeing while troubleshooting.
Maybe someone can help me from there.

---

### Post by odinb on 2007-07-02
ugm6hr referred to a link that brought up lots of trix, and one of them is to install FWCutter.

I was pulling my hair getting my Broadcombased Belkin-card to run under Feisty, and I had followed all the guides, or so I thought, and the system saw the cards, but no light on the LEDs on the card. After installing FWCutter, the LEDs on the card came on, and after a reboot of the machine, the card is now working, even with WPA using the KNetworkmanager-tool.

Good luck, and buy a Prism-based card next time, that is what I will do... (Bad bad Broadcom for not releasing drivers or any help on writing drivers for its chipset. Guess their loss since I will from now on avoid their chipset.)

---

### Post by ITdrummer on 2007-07-03
Ok, so i got the lights on the card to blink, and when i click on the network manager, my network "netgear" shows up.  But i cannot get it connected.  

What i had to do to ger it working was ndiswrapper_setup.
Any suggestions?

---

### Post by ITdrummer on 2007-07-03
Any suggestions on a wireless card that works flawlessly on linux (or at least with less complications than a broadcom chipset)?  I m thoroughly disappointed with my belkin card (on linux and windows)

---

### Post by ITdrummer on 2007-07-03
*bump*

---

### Post by ITdrummer on 2007-07-03
I still need help with my belkin card.  I installed NDISwrapper and got the link lights on my card to blink, but i still cannot connect to my network.

---

