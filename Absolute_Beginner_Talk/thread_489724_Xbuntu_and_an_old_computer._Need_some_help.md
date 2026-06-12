---
title: "Xbuntu and an old computer. Need some help"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by mrkip on 2007-07-01
Hi. Any help with this one would be appreciated. Cheers.

I've recently been given a neighbours old computer fix. The computer consist of a Pentium III (approx 633Mhz) with 256MB of RAM. It also has some ATI AGP Gfx card but i don't know what specific model it is. It also came with windows XP home.

Now I've had to re-format the HD due to the windows install being riddled with Trojans, malware,  and loads of other nasties (turns out he was running Limewire without any AV or a firewall).  After formatting the PC i asked my neighbour for his original XP disc, he told me he didn't have one and neither does the person who gave him the computer.

So i decided to install Xbuntu on his PC. Well I've got to say im really impressed with how it runs on his PC. I really think it will be ideal for my neighbour as he's complete beginner when it comes to computer's which means he's never got used to using any particular OS.

Xbuntu has installed fine and runs like a charm but im having problems which are;-


1.So far i have tried connecting to the internet  via Ethernet and USB to my NTL cable modem. I've also tried using an Asus WL-167G wireless usb adapter to try and connect to my home network as well. None of these have worked. I'm sure I've entered all my ISP's details correctly in the Network manager, I've also tried using a static and a dynamic IP address for the PC as well. But nothing i try seems to work, any suggestions?
2. To connect using Ethernet i had to install a D-Link 10/100Mbps PCI Adaptor due to the PC's motherboard having no native Ethernet connection/port. The manufacturer say that this card will work with Linux. How can i find out if this cards working correctly?
3. I've also installed a 'StarTech.com 4 Port PCI USB 2.0 Card' but im a unsure if it's working properly. How can i find out if it's running at USB 2.0 speeds in Xbuntu?
4.I also seem to be having problems writing to my USB pen drive even though it has a FAT32 partition on it. Has anyone any idea's why this is happening?
5.Also Xbuntu can't seem to shut down properly. When i try and shut it down it exit's out of the desktop and then seems to hang on the Xbuntu closing screen. No matter how long i leave the PC it never switches off, it just stay displaying the closing screen (the Xbuntu logo). How can i determine if this is a hardware or a software problem?

Please note that im a absolute beginner with Linux so please explain things easily.

Cheers.

---

### Post by logos34 on 2007-07-01
this might help you out:
**[COLOR="Blue"]https://help.ubuntu.com/community/TroubleShootingGuide[/COLOR]**

For usb,

sudo lshw

look for the usb section. 'configuration' line should show 'speed=480.0MB/s' (i.e. usb2.0)

---

### Post by ugm6hr on 2007-07-02
I use Xubuntu7.04, but am by no means an expert.  But will try and help.

1/2. Try plugging the ethernet cable into your cable modem, and then turning the computer on.  It should then connect to the modem automatically.  I'm not sure about getting onto the internet that way, but it should be possible (I use an ADSL router rather than simple modem).  I would be surprised if the ethernet card doesn't work with Linux.  

USB is always a trickier option - I don't know how to make that work, although there are some scattered how-to's for specific modems (but mainly ADSL rather than cable).

Wifi - I think that Asus adapter should work - it just needs to be set up (Stinger recommends Wifi radar): 
[http://ubuntuforums.org/showthread.php?t=330003&highlight=Asus+WL-167G](http://ubuntuforums.org/showthread.php?t=330003&highlight=Asus+WL-167G) (see Stinger post)
This is perhaps worth persevering with (I use Wicd / previously Network Manager with my laptops - so not sure how Wifi radar works - but probably similar - if you want to give Wicd a try I can help you through it).

4. What exactly is the problem?  Does it auto-mount (open Thunar File Manager) when you plug it in? Can you access / read files on it?  What happens when you try to write to it?

5. I have similar problems with the Hibernate option.  Try the following in Terminal to see if it can turn off manually```
sudo poweroff
```

---

### Post by mrkip on 2007-07-02
Cheers for the help.

1. I've tried connecting up the ethernet cable before startup but im still having the same problem.

2. I have had play about with wi-fi radar still no luck. Im getting no signal even though i enter all my router details correctly.
Im not going to bother trying to the USB option. I've just been reading 'Ubuntu for none Geeks'  which covers this method. It says its not for the faint of heart and should only be attempted if really nessesary

4. Ive sorted the pen drive problem. Dont know what i did but its working now.

5. Im still having the same problem even when using the 'sudo poweroff' command. It still does the same which is that it just hangs on the logo screen and the PC won't power off. 

I ran the sudo lshw command and (i think) it appears that the card seems to be running on some USB port at USB 2.0 speed's.

Here's the result for the sudo lshw. Im just hoping this might help me get to the bottom of my networking problems




             
    description: Computer
    product: VT82C694X
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal
  *-core
       description: Motherboard
       product: MS-6318
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG (04/06/00)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: SLOT 1
          size: 667MHz
          capacity: 800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-cache:0
          description: L1 cache
          physical id: 8
          slot: Internal Cache
          size: 32KB
          capacity: 32KB
          capabilities: synchronous internal write-back
     *-cache:1
          description: L2 cache
          physical id: 9
          slot: External Cache
          size: 256KB
          capacity: 2MB
          capabilities: synchronous external write-back
     *-memory
          description: Flash Memory
          physical id: 18
          slot: System board or motherboard
          size: 256MB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: BANK_0
             size: 128MB
        *-bank:1
             description: DIMM
             physical id: 1
             slot: BANK_1
             size: 128MB
     *-pci:0
          description: Host bridge
          product: VT82C693A/694x [Apollo PRO133x]
          vendor: VIA Technologies, Inc.
          physical id: d8000000
          bus info: pci@00:00.0
          version: c2
          width: 32 bits
          clock: 33MHz
          resources: iomemory:d8000000-dbffffff
        *-pci
             description: PCI bridge
             product: VT82C598/694x [Apollo MVP3/Pro133x AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: NV5 [RIVA TNT2/TNT2 Pro]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: 15
                size: 32MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=32 maxlatency=1 mingnt=5
                resources: iomemory:dc000000-dcffffff iomemory:de000000-dfffffff irq:11
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@00:07.0
             version: 1b
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=parport_pc latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@00:07.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE latency=32
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:d000-d00f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: ST320423A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 3.02
                   serial: 7EJ1N14N
                   size: 19GB
                   capacity: 19GB
                   capabilities: ata dma lba iordy smart pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma4 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 18GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 729MB
                      capacity: 729MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 729MB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD writer
                   product: _NEC DVD_RW ND-3550A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.05
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@00:07.3
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: ioport:d800-d81f irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Mouse
                   product: Optical USB Mouse
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@4:1
                   version: 3.40
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
              *-usb:1
                   description: Mass storage device
                   product: DataTraveler 2.0
                   vendor: Kingston
                   physical id: 2
                   bus info: usb@4:2
                   logical name: scsi0
                   version: 1.00
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: DataTraveler 2.0
                      vendor: Kingston
                      physical id: 0.0.0
                      bus info: scsi@0:0.0.0
                      logical name: /dev/sda
                      version: 1.00
                      size: 489MB
                      capabilities: removable
                      configuration: ansiversion=2
                    *-disc
                         physical id: 0
                         logical name: /dev/sda
                         size: 489MB
                         capabilities: partitioned partitioned:dos
                       *-volume
                            description: FAT16 partition
                            physical id: 1
                            logical name: /dev/sda1
                            capacity: 488MB
                            capabilities: primary bootable
        *-multimedia
             description: Multimedia audio controller
             product: ES1371 [AudioPCI-97]
             vendor: Ensoniq
             physical id: c
             bus info: pci@00:0c.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ENS1371 latency=32 maxlatency=128 mingnt=12
             resources: ioport:dc00-dc3f irq:10
        *-network
             description: Ethernet interface
             product: RTL8139 Ethernet
             vendor: D-Link System Inc
             physical id: e
             bus info: pci@00:0e.0
             logical name: eth0
             version: 10
             serial: 00:1b:11:48:fd:da
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
             resources: ioport:e000-e0ff iomemory:e0000000-e00000ff irq:11
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: f
             bus info: pci@00:0f.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: iomemory:e0001000-e0001fff irq:10
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: f.1
             bus info: pci@00:0f.1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: iomemory:e0002000-e0002fff irq:9
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: f.2
             bus info: pci@00:0f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: iomemory:e0003000-e0003fff irq:11
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: USB 2.0 Controller
             vendor: ALi Corporation
             physical id: f.3
             bus info: pci@00:0f.3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: iomemory:e0004000-e00040ff irq:9
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb
                   description: Generic USB device
                   product: 802.11g WLAN Drive
                   vendor: ASUS
                   physical id: 3
                   bus info: usb@5:3
                   version: 0.01
                   capabilities: usb-2.00
                   configuration: driver=rt2570 maxpower=300mA speed=480.0MB/s
        *-communication UNCLAIMED
             description: Communication controller
             product: HaM controllerless modem
             vendor: Ambient Technologies Inc
             physical id: 10
             bus info: pci@00:10.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: iomemory:e0005000-e0005fff ioport:e400-e4ff irq:10
     *-pci:1
          description: Host bridge
          product: VT82C686 [Apollo Super ACPI]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@00:07.4
          version: 20
          width: 32 bits
          clock: 33MHz
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@5
       logical name: rausb1
       serial: 00:11:d8:30:ba:9b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RT2500USBSTA driverversion=1.0.0 - BETA2 ip=192.168.1.7 link=yes multicast=yes wireless=RT2500USB WLAN

---

### Post by ugm6hr on 2007-07-02
OK. Let's try and get that wifi going:

Post the output from
```
lsusb
ifconfig
iwconfig
```

That might be enough to get it sorted - it appears there are (at least) 2 versions of the device (see No 60-62):
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/)

---

### Post by mrkip on 2007-07-03
thanx for taking the time to help

I've entered the commands you gave me and i get the following

_lsusb_

Bus 005 Device 002: ID 0b05:1706 ASUSTek Computer, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 002: ID 0930:6533 Toshiba Corp. 512M USB Stick
Bus 001 Device 001: ID 0000:0000

_ifconfig_

eth0      Link encap:Ethernet  HWaddr 00:1B:11:48:FD:DA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:11:48:FD:DA  
          inet addr:169.254.9.76  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:762 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60964 (59.5 KiB)  TX bytes:60964 (59.5 KiB)

rausb1    Link encap:Ethernet  HWaddr 00:11:D8:30:BA:9B  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe30:ba9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:302745 (295.6 KiB)  TX bytes:13468 (13.1 KiB)


_iwconfig_

lo        no wireless extensions.

eth0      no wireless extensions.

rausb1    RT2500USB WLAN  ESSID:"Tron"  Nickname:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-27 dBm  Noise level:-195 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ugm6hr on 2007-07-03
So it's this one (note usbid matches):
> 
Card: Asus WL-167G, 54mbps

    *
      Chipset: Ralink RT2500 USB
    *
      usbid: 0b05:1706
    *
      Driver: Cdrom, WinXP driver. (rt2500.sys, original at [www.ralinktech.com](www.ralinktech.com))
    *
      Other: Tested with Ndiswrapper 0.11, kernel 2.4.27, Knoppix. All thanks to ndiswrapper! B-)

#
Card: ASUS WL-167G

    *
      Chipset: RT2500USB
    *
      usbid: 0b05:1706
    *
      Driver: 2.00.01.0000 ([http://www.ralinktech.com](http://www.ralinktech.com))
    *
      Other: Mandriva LE 2005 (kernel-2.6.11), ndiswrapper-1.2rc1. Must install Kernel-Source 2.6-2.6.11-6mdk to compile ndiswrapper, use &#8220;ndiswrapper -d 0b05:1706 rt2500usb&#8221;... to get Hardware present, works at 54 Mb Great !! No need to recompile kernel, it just works fine. Thanks, Thanks !! Well done.


Option 1:
Ralink do Linux drivers, but I don't know how to install them.  This might give you a clue:
[http://ubuntuforums.org/showthread.php?t=398643](http://ubuntuforums.org/showthread.php?t=398643) (see final post)
The driver: 
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
You need the *RT2500USB(RT2571/RT2572) (source Code) * one (which has a readme)

Option 2:
The ndiswrapper option also appears to work according the ndiswrapper wiki entries above. 
The drivers (presumably extracting the .exe will provide the .inf and .sys files):
[http://www.ralinktech.com/ralink/Home/Support/Windows.html](http://www.ralinktech.com/ralink/Home/Support/Windows.html)
You need the *USB(RT257x/RT2671)* one

Try following this:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

But, **replace** *bcm43xx* with *rt2500usb* in Step 2.4, then repeat with *rt2570* and *rt2500*
And you can ignore the start of Step 2.5 (just put the rt2500 .inf and .sys in *~/drivers* - drivername=*rt2500*)

Hopefully one of those should get things going for you.  I have read that if you want ndiswrapper with WPA encryption, you have to Compile the latest ndiswrapper (see Step 4).

---

### Post by TravMan63 on 2007-07-03
> rausb1 Link encap:Ethernet HWaddr 00:11: D8:30:BA:9B
inet addr:192.168.1.7 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::211:d8ff:fe30:ba9b/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:302745 (295.6 KiB) TX bytes:13468 (13.1 KiB)

It appears this device's IP address is configured ok - and should be working

am I missing something else?

TM

---

### Post by ugm6hr on 2007-07-03
> **TravMan63 said:**
> It appears this device's IP address is configured ok - and should be working
Good point.  Missed that.

Think it might be an issue with rt2500usb vs rt2570 drivers, as here? [http://ubuntuforums.org/showthread.php?t=398643](http://ubuntuforums.org/showthread.php?t=398643)

Worth turning all security off on your wifi router (temporarily!) to see if it is an issue with encryption.

---

