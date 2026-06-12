---
title: "[SOLVED] mplayer crashes when going full screen"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by brokenhachi on 2008-02-02
here is the line i get when it crashes using "gmplayer"

> [ws] Error in display. -0.000 ct:  0.025 1505/1505  3%  8%  1.7% 9 0            
[ws]  Error code: 11 ( BadAlloc (insufficient resources for operation) )
[ws]  Request code: 141
[ws]  Minor code: 19
[ws]  Modules: flip_page


it happens whenever i try to change the origional size of the video or try to go fullscreen, and then the whole thing closes...

just for reference, i have an nvidia geforce fx go5200 video card..


any ideas?

---

### Post by jan quark on 2008-02-02
did you have tried another player? or is this problem limited only to gmplayer ?

are you running compiz?

what are your specs?

please post the result 
```
lspci
```
```
lshw
```

---

### Post by brokenhachi on 2008-02-02
yea i am running compiz, and i dont have any other video players except a DVD player.. ill try that in a min.


heres lspci


> ~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0a.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)


and lshw

> ~$ lshw
WARNING: you should run this program as super-user.
dave-laptop-linux         
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1010MB
     *-cpu
          product: Intel(R) Pentium(R) M processor 1400MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.9.5
          size: 1400MHz
          capacity: 1400MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up est tm2 cpufreq
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 21
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 21
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV34M [GeForce FX Go5200 64M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-network:0
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 83
                serial: 00:08:0d:a2:a9:d7
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=192.168.1.13 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
           *-network:1
                description: Wireless interface
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
                physical id: a
                bus info: pci@0000:02:0a.0
                logical name: eth1
                version: 04
                serial: 00:0c:f1:17:ea:9e
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
           *-pcmcia
                description: CardBus bridge
                product: ToPIC100 PCI to Cardbus Bridge with ZV Support
                vendor: Toshiba America Info Systems
                physical id: b
                bus info: pci@0000:02:0b.0
                version: 33
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=0 maxlatency=5 mingnt=128 module=yenta_socket
           *-system UNCLAIMED
                description: System peripheral
                product: SD TypA Controller
                vendor: Toshiba America Info Systems
                physical id: d
                bus info: pci@0000:02:0d.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0


---

### Post by jan quark on 2008-02-02
just a guess

turn off compiz and see if the problem still occurs

---

### Post by brokenhachi on 2008-02-02
alright well that works..... is there any way to make mplayer ignore that? so i can use compiz and mplayer at the same time?

---

### Post by jan quark on 2008-02-02
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/147453](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/147453)

it is a bug no idea if a fix is already done, does not seems so...

---

### Post by brokenhachi on 2008-02-02
hmmm... that sucks... maybe i should delete mplayer and use totem...?

---

### Post by philinux on 2008-02-02
> **brokenhachi said:**
> alright well that works..... is there any way to make mplayer ignore that? so i can use compiz and mplayer at the same time?

Install VLC from synaptic see if that works full screen with compiz.

---

### Post by jan quark on 2008-02-02
I always use this installation

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

t installs totem-xine and it also enables support for encrypted dvds

---

### Post by brokenhachi on 2008-02-02
> **philinux said:**
> Install VLC from synaptic see if that works full screen with compiz.

heres what i get when i even try to load a vid with VLC...

> ** (.:6518): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83
Failed to receive messages at scim_bridge_client_read_and_dispatch ()
An IOException occurred at handle_message ()
*** glibc detected *** vlc: double free or corruption (fasttop): 0x082045d8 ***



is there a way to get it to run with ignoring system resources? origionally compiz wouldnt run, but i ran it with a command that tells it to ignore how much vid ram i have.. and it works fine. maybe because i have alot of system memory that is free...?

---

