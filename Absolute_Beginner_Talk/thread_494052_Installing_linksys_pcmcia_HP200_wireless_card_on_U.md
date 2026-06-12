---
title: "Installing linksys pcmcia HP200 wireless card on Ubuntu"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by mpc000 on 2007-07-06
<<<scroll to the end for the solution>>>

Hello all,

I am completely new to the Ubuntu world, installed it just yesterday!

I have wired internet but I can't seem to be able to make my pcmcia Linksys HP200 wireless card to work!

I have tried following some advice I found on other posts but it doesn't seem to work for me.

I have gotten to the following point:

installed ndiswrapper and I can access System-Administration-Windows Wireless Drivers

I have copied all the .inf and .sys files from the pcmcia card cd to a /wifi directory I have made.

So I run the Windows Wireless Drivers utility (the window of the application would disappear as soon as I clicked on it but I removed/reinstalled ndiswrapper and it's ok now). I click to select my wifi drivers. I select it, click on install but nothing happens! 

It will not install anything! I have tried all different .inf files included in the cd but it does not install anything. The window on the left of the +install new driver remains completely blank!

The driver I am trying to install is the one described in the following post (this user had the same problem as me):

```

http://ubuntuforums.org/archive/index.php/t-331568.html

```

For him it worked, for me it will not install anything. After I click on install nothing happens!

I am running the latest Ubuntu release and have installed the latest ndiswrapper (I think 1.47).

I suspect that you might ask some of the following details so I put them here for reference

running  lshw (check out the last bit, it shows my adapter as UNCLAIMED, I can't find any information about UNCLAIMED situations on the forums).
```

    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 502MB
     *-cpu
          product: Intel(R) Pentium(R) M processor 1.60GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 6.13.8
          size: 798MHz
          capacity: 798MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up est tm2 cpufreq
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 04
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:b0080000-b00fffff ioport:1800-1807 iomemory:c0000000-cfffffff iomemory:b0000000-b003ffff irq:22
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 04
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: iomemory:34000000-3407ffff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1820-183f irq:19
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
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1840-185f irq:20
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Microsoft USB Wireless Mouse
                   vendor: Microsoft
                   physical id: 2
                   bus info: usb@2:2
                   version: 0.17
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=50mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1860-187f irq:21
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
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1880-189f irq:22
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:b0040000-b00403ff irq:19
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@06:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: iomemory:b0106000-b0106fff irq:17
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@06:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=128 maxlatency=4 mingnt=2
                resources: iomemory:b0107000-b01077ff iomemory:b0100000-b0103fff irq:23
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@06:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=128 maxlatency=4 mingnt=7
                resources: iomemory:b0104000-b0105fff irq:17
           *-system
                description: Generic system peripheral
                product: PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
                vendor: Texas Instruments
                physical id: 6.4
                bus info: pci@06:06.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=128 maxlatency=4 mingnt=7
                resources: iomemory:b0108000-b01080ff iomemory:b0107c00-b0107cff iomemory:b0107800-b01078ff irq:17
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@06:07.0
                logical name: eth0
                version: 10
                serial: 00:0a:e4:d6:66:24
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.64 latency=128 maxlatency=64 mingnt=32 multicast=yes
                resources: ioport:3000-30ff iomemory:b0108400-b01084ff irq:18
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@00:1e.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: ioport:1c00-1cff ioport:18c0-18ff iomemory:b0040800-b00409ff iomemory:b0040400-b00404ff irq:16
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@00:1e.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=0
             resources: ioport:2400-24ff ioport:2000-207f irq:18
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:1810-181f irq:21
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18a0-18bf irq:10
    [B] *-network UNCLAIMED
          description: Ethernet controller
          product: 88w8335 [Libertas] 802.11b/g Wireless
          vendor: Marvell Technology Group Ltd.
          physical id: 0
          bus info: pci@07:00.0
          version: 03
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: latency=0
          resources: iomemory:38000000-3800ffff iomemory:38010000-3801ffff irq:17[/B]

```

a last thing about ndiswrapper

when I do   ndiswrapper -l  it give me the following message:
```

The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found

```

so I do the   sudo apt-get install ndiswrapper-common and I get the following message:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

but when I do a   ndiswrapper -l  again I get the same message that it's not installed!

anyway, 

any help appreciated!

mpc

p.s some additions:
I checked out this webpage:
```

http://www.bizarnet.ro/wireless/asp/support.asp?lang=en

```

downloaded the HP200 linux driver and documentation but I got stuck, can't seem to make it work. At some point it asks me for the pcmcia directory but I don't seem to get it right! So I can't take it forward.


---solution---
finally I realised that the exact path plays a very important role in installing a driver with ndiswrapper. If you put a wrong path you dont get an error message but just "invalid driver", which means the path was wrong, not a wrong installation!

so I removed all the invalid drivers and I re-checked the chipset of my wi-fi card, realising I should download a different driver,   something ending in 8000c.inf and sys it was.

Then I installed it correctly and I also installed the network manager.

On top of that I disabled WAP and enabled WEP which is easier recognised and voila! im writing this through my wi-fi connection!

cheers
---end of solution------

---

### Post by limbourg31 on 2007-07-06
for ndiswrapper just do that, since one of the packages was removed, and the card is just not recongized at all, so try to reinstall it using ndiswrapper

---

### Post by mpc000 on 2007-07-06
> **limbourg31 said:**
> for ndiswrapper just do that, since one of the packages was removed, and the card is just not recongized at all, so try to reinstall it using ndiswrapper

Could you please explain a bit more on how? I am trying through the Windows Wireless Drivers but it will not install anything !!

How do I go on installing it through ndiswrapper? Do you mean by command line? How do I do that ?

if you need more info let me know!

Regards

---

### Post by limbourg31 on 2007-07-07
try installing all ndiswrapper packages through synaptic and make sure all dependencies are satisfied. Then see if the windows drivers work, since here ndiswrapper seems to be at fault, not the drivers themselves.

---

### Post by mpc000 on 2007-07-07
ok,

I went to synaptic, searched for ndiswrapper and then I

a) removed all 4 items
b) reinstalled them

the result now is that when I click on the Windows Wireless Drivers the window appears and disappears instantly, not letting me do anything.

any other ideas ?

btw, ndiswrapper -l gives me this:

```

lbcmnds : invalid driver!
lsbcmnds : driver installed
lsipnds : invalid driver!
lsmvnds : invalid driver!
lstinds : invalid driver!
wmp11nds : invalid driver!

```

I've tried installing different .inf's but nothing works. I can't seem to get a hardware present or whatever it's supposed to show when it works..

---

### Post by jdennis_99 on 2008-01-28
Hi,

I am also having problems with this card. I am trying to use the Linksys HP200 on the following:

Sony Vaio PCG-FX101
Intel Celeron 500MHz
512MB RAM
9.6GB Hard Drive
Kubuntu 7.10 (Gutsy)

I already have an Ethernet PC-Card - this was detected by Kubuntu installation, but I disconnected the wireless PC-Card during installation - I'd heard on the forums that installation can sometimes have problems with wireless devices.

So I'm now trying to install it.

I have installed ndiswrapper-common, ndiswrapper-utils-1.9 and ndisgtk via Adept. I have got the Windows XP drivers for the HP200 from the accompanying CD. I have then gone through the process described in [http://ubuntuforums.org/archive/index.php/t-331568.html](http://ubuntuforums.org/archive/index.php/t-331568.html) - using ndiswrapper to install the Windows XP drivers. There are three .inf files on the CD - I have tried installing all of them, both using the Windows Wireless Drivers GUI and via the terminal using ndiswrapper directly.

All of the drivers can be installed properly, and 'ndiswrapper -l' shows no problems. However, when the card is connected, my system doesn't recognise it - doesn't even acknowledge that it's connected.  Rebooting has no effect. ](*,)

Please help!!

---

### Post by jdennis_99 on 2008-02-01
Bump

---

