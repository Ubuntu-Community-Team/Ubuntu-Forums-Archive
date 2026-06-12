---
title: "[SOLVED] How to Tell if Wifi Card is Working? (Without Access Point)"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by JAYCEE1 on 2007-08-03
I put in my new Orinoce Gold PCMCIA Wifi card and rebooted my Dell D400. How can I tell if all is well with this card? I'm in a remote area with no Access Point around me to test the card.

I ran ifconfig and the TX bytes on eth3 gave a reading of 3k. (0.0 b on RX.) A few seconds later the same command gave a reading of 4k. Eth2 and eth4 are both 0.0 b.

Is there anything else that I need to do other than a reboot? 

Thanks!

---

### Post by GMachine_24 on 2007-08-03
at a command line prompt, type:

<code>

username@computer:~$ sudo lshw

</end code>

and see if your wireless card is listed in the output. You can paste your output here if you like.

however, since linux/wireless are so finicky, you will probably not know for sure if your laptop wireless works until you get back to 'civilization.'

also, i recommend installing the configuration software from this site:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

If you do, YOU MUST remove all ndis-related files from your computer or your wireless will not work.

--gm

---

### Post by JAYCEE1 on 2007-08-03
> **GMachine_24 said:**
> at a command line prompt, type:

<code>

username@computer:~$ sudo lshw

</end code>

and see if your wireless card is listed in the output. You can paste your output here if you like.

however, since linux/wireless are so finicky, you will probably not know for sure if your laptop wireless works until you get back to 'civilization.'

also, i recommend installing the configuration software from this site:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

If you do, YOU MUST remove all ndis-related files from your computer or your wireless will not work.

--gm

Thanks for the reply.

Here is the output of sudo lshw:

laptop           
    description: Portable Computer
    product: Latitude C400
    vendor: Dell Computer Corporation
    serial: 6G0ZB11
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-4700-1030-805A-B6C04F423131
  *-core
       description: Motherboard
       product: Latitude C400
       vendor: Dell Computer Corporation
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A03 (02/13/2002)
          size: 64KB
          capacity: 448KB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect pcmciaboot int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) III Mobile CPU       866MHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.11.1
          slot: Microprocessor
          size: 864MHz
          capacity: 1200MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KB
             capacity: 32KB
             capabilities: internal varies unified
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KB
             capacity: 512KB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 256MB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM_A
             size: 128MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM_B
             size: 128MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82830 830 Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 04
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:e0000000-e7ffffff iomemory:f4f80000-f4ffffff irq:11
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 00
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0 maxlatency=11
             resources: iomemory:d8000000-dfffffff iomemory:f4f00000-f4f7ffff
        *-usb
             description: USB Controller
             product: 82801CA/CAM USB (Hub #1)
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
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network:0
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth2
                version: 78
                serial: 00:06:5b:b6:4c:e5
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
                resources: ioport:ec80-ecff iomemory:fafffc00-fafffc7f irq:11
           *-pcmcia
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@02:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:f6000000-f6000fff irq:11
              *-network
                   description: Wireless PC Card
                   product: Version 01.01
                   vendor: 2Wire
                   physical id: 0
                   slot: Socket 0
                   resources: irq:3
           *-network:1
                description: Wireless interface
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@02:03.0
                logical name: eth3
                version: 03
                serial: 00:90:96:f8:64:2a
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=32 link=no multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:faffc000-faffdfff irq:11
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
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
             product: 82801CAM IDE U100
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
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:bfa0-bfaf iomemory:26000000-260003ff irq:11
           *-disk
                description: SCSI Disk
                product: HITACHI_DK23DA-2
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 00J2
                serial: 10XS3M
                size: 18GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 17GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 839MB
                   capacity: 839MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 839MB
                      capabilities: nofs
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: ioport:d800-d8ff ioport:dc80-dcbf irq:11
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             configuration: latency=0
             resources: ioport:d400-d4ff ioport:dc00-dc7f irq:11
  *-battery
       product: 4E369
       vendor: SANYO
       physical id: 1
       slot: Left Module Bay
       capacity: 40000mWh
       configuration: voltage=11.1V
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth4
       serial: 00:02:2d:93:af:8d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.42 link=no multicast=yes wireless=IEEE 802.11b
laptop:~$

---

### Post by GMachine_24 on 2007-08-03
Hi:

Ok, so this output:


[B]description: Wireless interface
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 3
bus info: pci@02:03.0
logical name: eth3
version: 03
serial: 00:90:96:f8:64:2a
width: 32 bits
clock: 33MHz
capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=32 link=no multicast=yes wireless=IEEE 802.11b/g
resources: iomemory:faffc000-faffdfff irq:11
*-isa[/B]

shows your computer knows it has a Broadcom wireless card located @ eth3 and that you installed the bcm43xx driver.


Now, do the rest of what I suggested, to wit:
[B]
also, i recommend installing the configuration software from this site:

[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

If you have installed the gnome network manager, remove it from your computer before installing the wicd package.

If you do, YOU MUST remove all ndis-related files from your computer or your wireless will not work.
[/B]

Run the WICD utility and see if it at least attempts to find any wireless networks in the area.

If you have to, search for ndis-related files and remove them.

Again, you will not know for sure whether your wireless is functional until you get somewhere that has wireless networks.

--gm

---

### Post by JAYCEE1 on 2007-08-04
I'm not able to access the internet on this computer. That's why I bought the Orinoco Wifi card. I have no Lan and dialup doens't configure under Ubuntu.

How can I tell if the Orinoco Gold Wifi card in the PCMCIA slot is working? 

I already know that the Broadcom isn't working and won't work until I can get this computer connected to the internet.

Thanks!

---

### Post by ugm6hr on 2007-08-04
> *-network
description: Wireless PC Card
product: Version 01.01
vendor: 2Wire
physical id: 0
slot: Socket 0
resources: irq:3

This is presumably the Orinoco card.  Unfortunately - it isn't associated with a driver at all at the moment.  Which means it won't work...

To see what the chipset is - tell us the output of:
```
lspci -nn
```

I think the Intersil / Orinoco / Prism cards are linux supported, but there has been a change in drivers.

PS: I'm sure the Broadcom can be made to work with ndiswrapper without internet.

---

### Post by JAYCEE1 on 2007-08-04
> **ugm6hr said:**
> This is presumably the Orinoco card.  Unfortunately - it isn't associated with a driver at all at the moment.  Which means it won't work...

To see what the chipset is - tell us the output of:
```
lspci -nn
```

I think the Intersil / Orinoco / Prism cards are linux supported, but there has been a change in drivers.

PS: I'm sure the Broadcom can be made to work with ndiswrapper without internet.

Here is the output of lspci -nn

```

laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82830 830 Chipset Host Bridge [8086:3575] (rev 04)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82830 CGC [Chipset Graphics Controller] [8086:3577] (rev 04)
00:02.1 Display controller [0380]: Intel Corporation 82830 CGC [Chipset Graphics Controller] [8086:3577]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB (Hub #1) [8086:2482] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
laptop:~$ 

```



Thanks!

---

### Post by ugm6hr on 2007-08-04
I'm a bit confused - was that lspci with the PCMCIA card plugged in?
There is no mention of an additional wifi card.  I believe the 3com is a wired connector.

Also - I made a bit of an error - I missed this in the lshw:
> *-network
description: Wireless interface
physical id: 2
logical name: eth4
serial: 00:02:2d:93:af:8d
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.42 link=no multicast=yes wireless=IEEE 802.11b

Which is actually the orinoco card.  

So what is the 2wire network entry? :confused:

EDIT:
Sorry - I kind of missed the point.... 
Please repost lspci with Orinoco card plugged in.
As for whether it works - I think there are some conflicts between orinoco and prism drivers in Feisty - and without trying it out with a router, I'm not sure you can be 100% certain it will work.  I am sure you can get it to work - but it might require blacklisting one or other driver.

---

### Post by JAYCEE1 on 2007-08-04
> **ugm6hr said:**
> I'm a bit confused - was that lspci with the PCMCIA card plugged in?
There is no mention of an additional wifi card.  I believe the 3com is a wired connector.

Also - I made a bit of an error - I missed this in the lshw:


Which is actually the orinoco card.  

So what is the 2wire network entry? :confused:

EDIT:
Sorry - I kind of missed the point.... 
Please repost lspci with Orinoco card plugged in.
As for whether it works - I think there are some conflicts between orinoco and prism drivers in Feisty - and without trying it out with a router, I'm not sure you can be 100% certain it will work.  I am sure you can get it to work - but it might require blacklisting one or other driver.

The Orinoco was plugged in when I ran lspci -nn as posted above.

The 2wire is the Orinoco card. 

When I goto System>Admin>System Monitor, Network history shows TX bytes going up every few seconds. I'm pretty sure something is going on with the card. I'm going to buy a cigarette lighter ac adaptor today and I'll ride around looking for an open connection.

I just though that there might be some configuration or network setting that is required to make the web browser look through the pcmcia Orinoco Wifi.

Being in a very remote location (I'm way out in the country), I wanted to get everything set up so that when I drive around with my Orinoco and external antenna, settings/configuration is not the problem. Wifi access points are going to be few and far between around here. If I ride around with the wrong settings, I don't know if my problem is lack of access points or bad settings: I haven't learned anything. 

Understand? I probably didn't make that clear above.

My guess is I won't know what I don't know until I get near an access point. I wanted to avoid riding around with bad settings is all.

I think all highway rest areas in Texas (where I am) have free and open Wifi. I may just hop over to the nearest rest area and see what happens.

Basically, I was trying to save myself driving 40-50 miles just to find out that the card wasn't "enabled" or that the proper box wasn't checked to make the Orinoco talk.

Thanks!

---

### Post by ugm6hr on 2007-08-04
Unfortunately, information on orinoco cards is a little limited - and it is definitely not currently working on your setup (since it is not given a network number on lshw).

Have a look at the following:
```
ifconfig
iwconfig
```

See what "interfaces" are open - because the Broadcom will still be.

Out of interest - where are you posting from if you don't have internet?

---

### Post by ugm6hr on 2007-08-04
While I'm here:

For the BCM4306 card - if you can download stuff elsewhere, use this:
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)
But only if you use Steps 1-3, then go direct to 11 (Feisty alternative option).

With this: [http://ubuntuforums.org/showthread.php?t=512364](http://ubuntuforums.org/showthread.php?t=512364) to help get past the parts that require internet (i.e. the apt-get instruction for ndiswrapper).

---

### Post by JAYCEE1 on 2007-08-04
> **ugm6hr said:**
> Unfortunately, information on orinoco cards is a little limited - and it is definitely not currently working on your setup (since it is not given a network number on lshw).

Have a look at the following:
```
ifconfig
iwconfig
```

See what "interfaces" are open - because the Broadcom will still be.

Out of interest - where are you posting from if you don't have internet?

My old IBM T23 running Fedora FC5 can access the internet through dialup. My new Dell can access the internet through Lan or wireless. I have niether. Dialup doesn't configure on the new Ubuntu/Dell (or that's what I have read here) so I run the commands on the Dell, paste the output to a flash drive and use the T23/dialup to post on here.

Here is iwconfig:

```

laptop:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

eth3      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth4      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by JAYCEE1 on 2007-08-04
Here is ifconfig:

```

laptop:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:06:5B:B6:4C:E5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xec00 

eth3      Link encap:Ethernet  HWaddr 00:90:96:F8:64:2A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9058 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:380436 (371.5 KiB)
          Interrupt:11 Base address:0xc000 

eth4      Link encap:Ethernet  HWaddr 00:02:2D:93:AF:8D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0xe100 

eth2:avah Link encap:Ethernet  HWaddr 00:06:5B:B6:4C:E5  
          inet addr:169.254.8.136  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48962 (47.8 KiB)  TX bytes:48962 (47.8 KiB)

laptop:~$ 


```

---

### Post by JAYCEE1 on 2007-08-04
The Broadcom is built in and the Orinoco is a PCMCIA card. I cannot currently connect this Dell/Ubuntu 7.04 to the internet at all to download utilities to install these cards. 

I'm stuck on dialup and I'm trying to activate Wifi with no access to the internet other than dialup on a completely seperate machine. The Dell/Ubuntu has no CD/DVD drive. I have a flash memory drive (512M) that I can use on both machines (the Dell/Ubuntu-no-internet and the T23/Fedora which is on dialup).

I'm in a bit of a pickle with all of this.

Thanks!

---

### Post by ugm6hr on 2007-08-04
> **JAYCEE1 said:**
> The Broadcom is built in and the Orinoco is a PCMCIA card. I cannot currently connect this Dell/Ubuntu 7.04 to the internet at all to download utilities to install these cards. 

I'm stuck on dialup and I'm trying to activate Wifi with no access to the internet other than dialup on a completely seperate machine. The Dell/Ubuntu has no CD/DVD drive. I have a flash memory drive (512M) that I can use on both machines (the Dell/Ubuntu-no-internet and the T23/Fedora which is on dialup).

I'm in a bit of a pickle with all of this.

Thanks!

OK. That's clear now.  Will you need to access any WPa encrypted networks with wifi when you are travelling?  If not - the internal wifi should be workable easily:
Download these (assuming you have the i386 rather than AMD64 Ubuntu), or find the packages on the Ubuntu CD if the IBM has a CD drive:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb&md5sum=e8876c665294254b55b32c02f629ac78&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb&md5sum=e8876c665294254b55b32c02f629ac78&arch=i386&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main)
Just download them on the IBM, USB them over to the Dell and copy to /var/cache/apt/archives (you will have to use command *gksudo nautilus* to do this.
Also - download this and copy to /home/*user*/ on Dell:
[http://home.nc.rr.com/thehinnants/stuff/drivers/bcmwl5.zip](http://home.nc.rr.com/thehinnants/stuff/drivers/bcmwl5.zip)
Extract this (double-click should do it) to /home/*user*/bcmwl5/
Put the bcmwl5a files in /home/*user*/bcmwl5a/ in case you need to try them.

Then follow instructions here:
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)
But only use Steps 1-3, then go direct to 11 (Feisty alternative step option) and continue from there.  Also - make sure you follow the advice in Problem 4.

This should get the internal card up and running, meaning that you will potentially have a backup with Orinoco when you go out driving.

---

### Post by JAYCEE1 on 2007-08-04
> **ugm6hr said:**
> 
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb&md5sum=e8876c665294254b55b32c02f629ac78&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb&md5sum=e8876c665294254b55b32c02f629ac78&arch=i386&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main)
Just download them on the IBM, USB them over to the Dell and copy to /var/cache/apt/archives (you will have to use command *gksudo nautilus* to do this.


Can I just copy and paste under the file browser or do I need to do a "make archive"?

(I just copied and pasted.)

Thanks!

---

### Post by ugm6hr on 2007-08-04
> **JAYCEE1 said:**
> Can I just copy and paste under the file browser or do I need to do a "make archive"?

(I just copied and pasted.)

Thanks!

Not sure what you mean by make archive.

Fairly simple:
Click on links.
Use File Manager Nautilus to copy and paste to location, as described.

---

### Post by JAYCEE1 on 2007-08-04
Step 11, Fiesty seems to require an internet connection which I do not have on the Dell.


```

sudo apt-get install ndiswrapper-utils-1.9

```

Reply is "could not resolve us.archive.ubuntu.com"

Did I miss something?

---

### Post by JAYCEE1 on 2007-08-04
> **ugm6hr said:**
> Not sure what you mean by make archive.

Fairly simple:
Click on links.
Use File Manager Nautilus to copy and paste to location, as described.

I meant "create archive" which is an option under contextual menu when you right click.

I copied and pasted the files to the archives.

---

### Post by ugm6hr on 2007-08-04
> **JAYCEE1 said:**
> Step 11, Fiesty seems to require an internet connection which I do not have on the Dell.

```

sudo apt-get install ndiswrapper-utils-1.9

```

Reply is "could not resolve us.archive.ubuntu.com"

Did I miss something?

Look in /var/cache/apt/archives again - you sure you put the files there???
ndiswrapper-common_1.38-1ubuntu1_all.deb
ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb

If not - do that first.

If so - then copy them back to your home directory and double-click on them in the order above.

---

### Post by ugm6hr on 2007-08-04
> **JAYCEE1 said:**
> I meant "create archive" which is an option under contextual menu when you right click.

I copied and pasted the files to the archives.

No - do not create archive. Copy to the location I gave.

---

### Post by JAYCEE1 on 2007-08-04
> **ugm6hr said:**
> Look in /var/cache/apt/archives again - you sure you put the files there???
ndiswrapper-common_1.38-1ubuntu1_all.deb
ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb

If not - do that first.

If so - then copy them back to your home directory and double-click on them in the order above.

One of the files wasn't there.

Redoing.

---

### Post by JAYCEE1 on 2007-08-04
Both files were in the archive this time. 

When I go to step 11, fiesty alternative, apt-get attempts to connect to the internet. 

I cannot connect to the internet on that computer.

---

### Post by JAYCEE1 on 2007-08-04
Would I need to first download the tar onto my flash drive then move it over to the Dell?

---

### Post by ugm6hr on 2007-08-04
> **JAYCEE1 said:**
> Both files were in the archive this time. 

When I go to step 11, fiesty alternative, apt-get attempts to connect to the internet. 

I cannot connect to the internet on that computer.

No worries.  

Bizarre that apt-get doesn't see them in that location - must be something to do with your sources.  But it doesn't matter.

You could try from Synaptic Package Manager - search for ndiswrapper - and then mark the 2 packages ndiswrapper-common and ndiswrapper-utils-1.9 for installation.

If that doesn't work either - just double-click on the 2 files in order.  Unfortunately, they need to be in your home directory for it to work like this - so copy them both to /home/user and double-click.

---

### Post by ugm6hr on 2007-08-04
> **JAYCEE1 said:**
> Would I need to first download the tar onto my flash drive then move it over to the Dell?

which tar?  there are only 3 files you need.
2 ndiswrapper & 1 windows driver zip file.
you only need the 2 ndiswrapper files for step 11.
you need the unzipped drivers in the *correct* locations (i.e. the normal and "a" files in separate folders) for step 12.

---

### Post by ugm6hr on 2007-08-04
Oh - and just to be sure...

You are using the i386 (not 64-bit) Ubuntu, aren't you?

---

### Post by JAYCEE1 on 2007-08-04
> **ugm6hr said:**
> which tar?  there are only 3 files you need.
2 ndiswrapper & 1 windows driver zip file.
you only need the 2 ndiswrapper files for step 11.
you need the unzipped drivers in the *correct* locations (i.e. the normal and "a" files in separate folders) for step 12.

I made the directory for the zipped file per your directions. I double-clicked the zipped file and it didn't unzip. I tried using gunzip from the command line and it said:

```
gunzip: bcmwl5.zip: unknown suffix -- ignored
```

Could that be the problem?

---

### Post by ugm6hr on 2007-08-04
> **JAYCEE1 said:**
> I made the directory for the zipped file per your directions. I double-clicked the zipped file and it didn't unzip. I tried using gunzip from the command line and it said:

```
gunzip: bcmwl5.zip: unknown suffix -- ignored
```

Could that be the problem?

Have you managed to install ndiswrapper yet?  You don't need the zip file for that stage.

Not sure why you can't extract the zip file - it works fine on my computer.

---

### Post by JAYCEE1 on 2007-08-04
> **ugm6hr said:**
> Have you managed to install ndiswrapper yet?  You don't need the zip file for that stage.

Not sure why you can't extract the zip file - it works fine on my computer.

When I double clicked ndiswrappe-common from home/user file it says

"cannot open ndiswrapper-common The filename indicates that this file is of type "Software package". The contents of the file indicate it is of "plain text". 

To open, rename the file with the correct extension for plain text document. Or use open with menu to choose a specific application for the file."

---

### Post by JAYCEE1 on 2007-08-04
Also, the icon of ndiswrapper-common has changed from a package to a text file icon.

Ndiswrapper-utils still shows a box / package for an icon.

---

### Post by ugm6hr on 2007-08-04
> **JAYCEE1 said:**
> I made the directory for the zipped file per your directions. I double-clicked the zipped file and it didn't unzip. I tried using gunzip from the command line and it said:

```
gunzip: bcmwl5.zip: unknown suffix -- ignored
```

Could that be the problem?

I don't use gunzip - but I am sure Ubuntu has a default unzip package installed.  I use Xubuntu - so I'm not sure what it's called.  Can you unzip on the IBM?  If so - unzip there and transfer the files.

---

### Post by ugm6hr on 2007-08-04
> **JAYCEE1 said:**
> Also, the icon of ndiswrapper-common has changed from a package to a text file icon.

Ndiswrapper-utils still shows a box / package for an icon.

Clearly there is a problem with the ndiswrapper-common file.  You will have to redownload it and transfer again.

---

### Post by JAYCEE1 on 2007-08-04
OK, I worked out several small problems.

I checked the properties of the ndiswrapper-common file on the Dell and it read 0.0k. On the IBM it showed to be about 18k. I retransferred it using the flash memory stick and finally got it to show up on the Dell as 18k.

This may have been the problem with the zip file also. I unzipped it on the IBM and moved everything over to the Dell's home/user file.

I went back through the steps as described in the "HOWTO: Broadcom 4306 With Ndiswrapper 54 Mbps" post and that went as it should, more or less.

I was then able to connect to a "network" that was the same name as my computer. It said I was connected to a wireless network but I was not able to surf the net. There certainly is no access point around here. 

I'll post lspci outputs and a few others later.

I think I'm pretty far along now.

---

### Post by JAYCEE1 on 2007-08-04
I ran all of these with my Orinoco PCMCIA card plugged in. I'm not sure if I should have done that or not.

Here is the output. I didn't get the expected output after "ndiswrapper -l" which is very near the bottom.

```

dellc400@dellc400-laptop:~$ gksudo nautilus(nautilus:13126): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension

** (nautilus:13126): WARNING **: bookmark uri is file:///home/dellc400, but expected file:///

--- Hash table keys for warning below:
--> file:///

--- Hash table keys for warning below:
--> file:///

(nautilus:13126): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:13126): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)
dellc400@dellc400-laptop:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ndiswrapper-common
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/50.1kB of archives.
After unpacking 225kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  ndiswrapper-common ndiswrapper-utils-1.9
Install these packages without verification [y/N]? y
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 104929 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.38-1ubuntu1_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb) ...
Setting up ndiswrapper-common (1.38-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.38-1ubuntu1) ...
dellc400@dellc400-laptop:~$ ndiswrapper -l
dellc400@dellc400-laptop:~$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
dellc400@dellc400-laptop:~$ sudo modprobe ndiswrapper
dellc400@dellc400-laptop:~$ 

```


Next I removed the Orinoco PCMCIA from the slot and restarted the computer. After restart, the "wireless" was missing from menu System>Admin>Network.

Here is what I did next. "forcing parameter IBSSGmod..." was an unexpected response.

This time I get the expected response after "ndiswrapper -l"


```

dellc400@dellc400-laptop:~$ ndiswrapper -l
dellc400@dellc400-laptop:~$ sudo apt-get install ndiswrapper-utils-1.9
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dellc400@dellc400-laptop:~$ sudo ndiswrapper -i /home/dellc400/bcmwl5.inf
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
dellc400@dellc400-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
dellc400@dellc400-laptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

dellc400@dellc400-laptop:~$ sudo modprobe ndiswrapper
dellc400@dellc400-laptop:~$ 

dellc400@dellc400-laptop:~$ sudo gedit /etc/network/interfaces
Password:
dellc400@dellc400-laptop:~$ nm-applet
** Message: <information>       You are now connected to the wireless network 'dellc400-laptop'.


```





When I goto menu System -> Admin -> Network I do not get an "activate" or "deactivate" button. I only have "properties" buttons for wireless connection, wired connection, and modem connection. The little check box to the left of the wired connection is checked. The little check box next to the wireless connection has a dash [a hyphen] in the box. I cannot check the wireless box even when the wired connection box is unchecked.

Here is the output of sudo lshw -C network:

```

dellc400@dellc400-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth2
       version: 78
       serial: 00:06:5b:b6:4c:e5
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
       resources: ioport:ec80-ecff iomemory:fafffc00-fafffc7f irq:11
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: wlan0
       version: 03
       serial: 00:90:96:f8:64:2a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Linksys,07/17/2003, 3.30.15.0 latency=32 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:faffc000-faffdfff irq:11
dellc400@dellc400-laptop:~$ 


```

Here is lspci -nn

```

dellc400@dellc400-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82830 830 Chipset Host Bridge [8086:3575] (rev 04)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82830 CGC [Chipset Graphics Controller] [8086:3577] (rev 04)
00:02.1 Display controller [0380]: Intel Corporation 82830 CGC [Chipset Graphics Controller] [8086:3577]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB (Hub #1) [8086:2482] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

```

ifconfig:


```

dellc400@dellc400-laptop:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:06:5B:B6:4C:E5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xec00 

eth2:avah Link encap:Ethernet  HWaddr 00:06:5B:B6:4C:E5  
          inet addr:169.254.8.136  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5792 (5.6 KiB)  TX bytes:5792 (5.6 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:F8:64:2A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:3962 (3.8 KiB)
          Interrupt:11 Memory:faffc000-faffe000 

```

iwconfig:

```

dellc400@dellc400-laptop:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:14 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```




Thanks!

---

### Post by ugm6hr on 2007-08-05
You should have network manager installed.  It is an icon that looks like 2 computers in the top right corner.  Is it there?

Try clicking on it and see what happens.  It should come up with a list of access points - obviously none in your case.  

Also - try right-clicking on it - it should bring up an option for "Manual config" or something similar.  If you go to that - it should allow you to manually configure your wifi (with Orinoco taken out!)  Make sure the "Enable roaming" option is ticked.

Then - I think you *should* be good to go....

One other thing to confirm functioning:```
iwlist scan
``` This should list no access points - or something like that.

---

### Post by JAYCEE1 on 2007-08-05
I ran iwlist scan and it said "no scan results" for wlan0. Then I played around with the network manager icon. (It now looks like 3 signal strength bars. Yesterday it looked like two computers.)

I selected manual, and connect and a few others. Then it gave me a choice of connecting to a wireless network called "gaeyakbwcifitnxyvwclovvqbrpsbilj." (I don't know where this network came from. I didn't put it in there.) I connected to that network and ran iwlist again. This time it gave me a reading for wlan0. Lo and eth2 both still say "interface doesn't support scanning."

```

wlan0 scan completed:

Cell 01 - Address: AA:59:2C:53:C9:69
              ESSID: "gaeyakbwcifitnxyvwclovvqbrpsbilj."
              Protocol:IEEE 802.11b
              Mode: Ad-hoc
              Frequency:2.462 Ghz (Channel 11)
              Quality: 100 Signal Level: 0 Noise Level:160
              Encryption Key: off
              Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24     
              Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
              Extra:bcn_int=100
              Extra:atim=0


```

When I saw the above, I tried to open a Firefox browser to see if I had a connection. My computer locked up before the browser finished opening.

I had to fat-finger in the above output since the computer locked up. There may be a minor typo or two.

I'll restart it now and see what happens next.

---

### Post by ugm6hr on 2007-08-05
That iwlist scan suggests there is a network somewhere near enough to you to pick up a signal.

Although not sure what to make of the quality / signal / noise entries there - they should be in different units - e.g.:
```
          Cell 04 - Address: 00:14:6C:D4:47:A8
                    ESSID:"network270"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=9/94  Signal level=-86 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
```

---

### Post by JAYCEE1 on 2007-08-05
Do I need to scan for available wireless networks or is that automatically displayed under network manager?

Should I open a web browser to test for a connection or should I do something else, like ping?

---

### Post by ugm6hr on 2007-08-05
> **JAYCEE1 said:**
> Do I need to scan for available wireless networks or is that automatically displayed under network manager?

Should I open a web browser to test for a connection or should I do something else, like ping?

Network Manager should list all SSID in range - so you could just try connecting to that same one you tried before.  The only reason I suggested iwlist was to ensure that it didn't return a "Interface doesn't support scanning" message - which it doesn't now.  Which does in fact suggest that it might be working.

One other thing to check - is to make sure ndiswrapper is listed as the *driver=ndiswrapper* from:
```
lshw -C network
```

Then either try a webpage or
```
ping google.com
```

On second thought - in case the access point is not actually connected to the internet - just check the output from:```
iwconfig
```
It should list something like:
```

ath0      IEEE 802.11g  ESSID:"MySSID"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate:18 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/94  Signal level=-57 dBm  Noise level=-93 dBm
          Rx invalid nwid:191985  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by JAYCEE1 on 2007-08-05
lshw -C network shows that ndiswrapper driver is being used.

I was able to connect to another wireless network with an extremely long name but different than the first network.

When I pingged google.com from this other wireless network, my whole computer locked up again.

It seems that everytime I try to use a wireless network my computer freezes.

Is this a known problem?

---

### Post by ugm6hr on 2007-08-05
> **JAYCEE1 said:**
> 
Is this a known problem?
Definitely not.
Did you check iwconfig?
And possibly it's Network Manager misbehaving (although I can't see why).  I haven't used NM for a while now.  :-k

---

### Post by JAYCEE1 on 2007-08-05
Just did it again.  This time I didn't have a chance to ping. As soon as I connected to the wireless network the computer locked up.

Everytime I connect to one of these mysterious netwoks with the long name my computer freezes.

---

### Post by ugm6hr on 2007-08-05
> **JAYCEE1 said:**
> Just did it again.  This time I didn't have a chance to ping. As soon as I connected to the wireless network the computer locked up.

Everytime I connect to one of these mysterious netwoks with the long name my computer freezes.

Hmm.. must be something to do with the network you are trying to connect to.  I don't know what the issue is, I'm afraid.

---

### Post by JAYCEE1 on 2007-08-05
> **ugm6hr said:**
> Definitely not.
Did you check iwconfig?
And possibly it's Network Manager misbehaving (although I can't see why).  I haven't used NM for a while now.  :-k

Here is iwconfig after a fresh reboot with no network connection established:

```

dellc400@dellc400-laptop:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:16 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dellc400@dellc400-laptop:~$ 



```

---

### Post by ugm6hr on 2007-08-05
I'm afraid I have no other way of checking if it works - other than trying it out on a genuine open network now.  It *should* work now.

Just a thought.... :-k

What OS do you run on the IBM?  And will it take the Orinoco card?  If so - you could try and create a home network between the 2 laptops via wifi.... I have never done it - but it must be possible - that way you could check that both cards work.

---

### Post by JAYCEE1 on 2007-08-05
> **ugm6hr said:**
> I'm afraid I have no other way of checking if it works - other than trying it out on a genuine open network now.  It *should* work now.

Just a thought.... :-k

What OS do you run on the IBM?  And will it take the Orinoco card?  If so - you could try and create a home network between the 2 laptops via wifi.... I have never done it - but it must be possible - that way you could check that both cards work.

I was just thinking of doing the same thing.

On the IBM I run Fedora Linux (FC5).

I use the PCMCIA dialup card on the IBM. Ihaven't yet plugged the Orinoco into it yet.

---

### Post by ugm6hr on 2007-08-05
> **JAYCEE1 said:**
> I was just thinking of doing the same thing.


These might prove useful:
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)
[http://www.fs-security.com/docs/dhcp.php](http://www.fs-security.com/docs/dhcp.php)

You can test the setup without internet by using (or use whatever IP's you chose):
```
ping *192.168.0.1*
```

Of course - you have to get the Orinoco working in Fedora!

---

### Post by JAYCEE1 on 2007-08-08
I finally bought my DC to AC converter and drove over to the highway rest area with both laptops. The wireless works fine on both. I was able to look at a website with no problem on the Dell. I put the Orinoco in the IBM and it connected itself before I could get the network configuration window open. Both work great!

Thanks for all of the help!

---

### Post by ugm6hr on 2007-08-08
How about that!

From wanting 1 wifi connection to having 2 working :)

Always pleased to hear that something I have helped with has worked :popcorn:

---

