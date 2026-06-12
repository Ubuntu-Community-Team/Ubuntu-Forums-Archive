---
title: "Error on restarting X-server"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Vlizzard on 2007-10-01
I recently installed ubuntu edgy on a toshiba laptop.  I updated it to feisty right away through the update manager.  I enabled desktop effecdts and they seemed to work fine.   I was then going to try to install compiz fusion for the desktop.  I found a howto video on youtube, and installed it without a problem.  When i run it though, my windows cease to have borders!  Otherwise it seemed to work alright.  So I went and searched for other howtos to see if  I missed something.  Some of the others talked about updating the nvidia drivers.  I used the code below to get the latest nvidia driver and install it.  

Code:
sudo apt-get install nvidia-glx
sudo nvidia-xconfig --add-argb-glx-visuals --composite

The website then said to restart the x-server by pressing Ctrl + Alt + Backspace.  I did this and a blue error screen came up that said starting the graphical interface failed and that it was probably a problem with the x-server configuration.  It then gives you more info and finally gets you to the command prompt.  I tried restarting the computer and still get the error screen.  I have also tried to reconfigure the x-server with the code:

sudo dpkg-reconfigure xserver-xorg

but I don't know what graphics driver to use from the provided list or other settings needed.  What i'm wondering is if anyone knows how to fix the x-server or if it can be reset to a default? Or is it better to just reinstall Ubuntu from scratch?

---

### Post by Pumalite on 2007-10-01
Accept most defaults and choose 'vesa' as your driver. Later, once IN the system you can worry about the rest.

---

### Post by Hospadar on 2007-10-01
If your laptop has an nvidia card you can also use the "nv" drivers, these are the community-written open source drivers for nvidia and work well for general-purpose stuff (Although you'll want to get the real nvidia drivers later for better performance and 3d)

As for actually getting the right nvidia drivers I would use the envy script.  ctrl-alt-F1 to get to a command line and then ```
sudo apt-get install envy
sudo envy -t
```
and then select "remove" "clean" and then "install" for nvidia drivers

You might need some extra repos, i'm sure if you google "envy nvidia ubuntu" or something like that you can find anything on that you need to know.

---

### Post by houstonbofh on 2007-10-01
I would not recommend Envy to "Absolute Beginners."  It has a place, but it will also generate a lot of problems on October 18th.  It is one of those "If you have to ask, you shouldn't use it" kind of things to me.

---

### Post by Vlizzard on 2007-10-02
Thank you Pumalite!  I got it working again, and I think i can get the settings I had back through system preferences.   I have a general question though, if my laptop has an intel card, what driver should I install?  When i chose "vesa" as my driver, was i installing a vesa driver?  Sorry if these are dumb questions, i'm pretty new to computers and ubuntu.

---

### Post by Pumalite on 2007-10-02
Vesa is a jack of all trades that allows you to get in the system, then, later you can fix things to your liking. I'm not familiar with Intel Integrated, but let's check what you have: post:
lshw

---

### Post by Vlizzard on 2007-10-04
WARNING: you should run this program as super-user.
steve-laptop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 502MB
     *-cpu
          product: Genuine Intel(R) CPU           T2050  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor est tm2 xtpr cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:dc100000-dc17ffff ioport:1800-1807 iomemory:c0000000-cfffffff iomemory:dc200000-dc23ffff irq:11
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: iomemory:dc180000-dc1fffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:dc240000-dc243fff irq:22
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@05:00.0
                logical name: eth1
                version: 02
                serial: 00:13:02:80:af:9c
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=10.0.0.142 latency=0 multicast=yes wireless=IEEE 802.11g
                resources: iomemory:da000000-da000fff irq:18
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
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
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
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
                   product: Microsoft Wireless Optical Mouse
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.07
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1860-187f irq:18
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
             product: 82801G (ICH7 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1880-189f irq:17
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
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:dc444000-dc4443ff irq:19
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@07:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:dc007000-dc007fff irq:18
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 6.1
                bus info: pci@07:06.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=128 maxlatency=4 mingnt=2
                resources: iomemory:dc006000-dc0067ff iomemory:dc000000-dc003fff irq:16
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@07:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=128 maxlatency=4 mingnt=7
                resources: iomemory:dc004000-dc004fff irq:18
           *-system
                description: Generic system peripheral
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@07:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=128 maxlatency=4 mingnt=7
                resources: iomemory:dc006800-dc0068ff irq:18
           *-network
                description: Ethernet interface
                product: PRO/100 VE Network Connection
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@07:08.0
                logical name: eth0
                version: 02
                serial: 00:a0:d1:44:ed:fb
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 multicast=yes
                resources: iomemory:dc005000-dc005fff ioport:4000-403f irq:21
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:18b0-18bf irq:20
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18c0-18df irq:10

---

### Post by Pumalite on 2007-10-04
You might want to try:

sudo apt-get install 915resolution

---

### Post by Vlizzard on 2007-10-05
Thanks!  I installed the 915resolution and all seemed to go okay.

---

### Post by Pumalite on 2007-10-05
Good! You are welcome. Good luck.

---

