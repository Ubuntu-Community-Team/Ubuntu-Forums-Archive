---
title: "How can I get a crazy desktp?:)"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by yngvrr on 2008-04-21
Ive had Ubuntu for about a week now and its working good. Thanks to all the help Ive had from this forum Ive been able to get everything working that I need working. Now I was thinking about trying to make it look better.. Ive seen on youtube videos people send in of their awsome desktop.. great effects where windows burn instead of closing and the desktop is 3d so instead of.. well someone must know what I'm talking about... anyway... can anyone help me??

---

### Post by Atro on 2008-04-21
go to System>Administration> Synaptic Software> search for "compiz manager"
mark it, install it and then press Alt+F2 and type : compiz-manager and run it. This gives you whole bunch of options to change the look you got.
There is another one called Beryl which I think has this fire stuff

---

### Post by Hairy_Palms on 2008-04-21
go to 
System->Administration->Synaptic 
then find and install compizconfig-settings-manager
then run it from the menu or with the command ccsm, then customise to your hearts content :D

---

### Post by phidia on 2008-04-21
Make sure you have the best driver for your video card to do that check the stickies at the [mutimedia and video forum]("http://ubuntuforums.org/forumdisplay.php?f=138").

After you have that working for 3D effects you can decide which effects package you want.
There are several eye candy managers you can search compiz, beryl, emerald, gtk...
Maybe check [this thread]("http://ubuntuforums.org/showthread.php?t=722335&highlight=beryl+compiz") and parent

---

### Post by yngvrr on 2008-04-21
Okey.. I get thee different compiz-things to pick from.. 

1. Compiz - "OpenGL composition manager
compiz provides support for compositing X windows using OpenGL. This allows
clients to modify what is drawn to the screen before it happens and for this
to be hardware accelerated."

2. Compiz-gnome - "Gnome window decorator and libraries for Compiz
This is a gnome window decorator that can be used with the compiz composition
and window manager."

3. Compiz-kde - "KDE window decorator for Compiz
This is a KDE window decorator that can be used with the compiz composition
and window manager."

Should I take all or just one..? wich one?

---

### Post by fatality_uk on 2008-04-21
Are you running Ubuntu or Kubuntu? Which version?
If your running Ubuntu you want the compizconfig-settings-manager

---

### Post by aktiwers on 2008-04-21
This link is awesome for beginners! 
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by yngvrr on 2008-04-21
Well.. acording to my Synaptic package manager compizconfig-settings-manager does not exist... can I get this through the terminal.. with an easy command perhaps..?

---

### Post by aktiwers on 2008-04-21
Did you enable 3 part repositories?
[https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)

---

### Post by Michael.Godawski on 2008-04-21
Terminal installation:
```

sudo apt-get install compizconfig-settings-manager
```

By the way what is your graphic card?

---

### Post by audwan on 2008-04-21
I believe it is called compizconfig-settings-manager. You could use Synaptic, or these commands to install:
```

sudo aptitude update
sudo aptitude install compizconfig-settings-manager

```

---

### Post by yngvrr on 2008-04-21
I have no idea what my grafikcard.. I have tried everything suggested but nothing works. When I try to enable the repositories I go to system/administration/softwere properties and add (universe) and/or (multiverse).. eitherway it does not work... Maybe bacause when I add them in repositories they dont stick that way.. I can add them again and again.. and nothing happens... is there somthing Im doing wrong?

---

### Post by yngvrr on 2008-04-21
He.. I didnt see the last message when I wrote my last... Anyway.. I put in this command as suggested : "sudo aptitude update" and a lot of things happened.. then I put in the other one : "sudo aptitute install compizconfig-settings-manager" and this is what happened : 
[SIZE="2"]"Reading package lists... Done
 Building dependency tree... Done
 initialising package states... Done
 Building tag database... Done
Couldn't find any package whose name or description matched "compizgonfig-settings-manager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and ö not upgraded.
Need to get OB of archives. Afterunpacking OB will be used."[/SIZE]

---

### Post by phidia on 2008-04-21
> **yngvrr said:**
> I have no idea what my grafikcard.. I have tried everything suggested but nothing works. When I try to enable the repositories I go to system/administration/softwere properties and add (universe) and/or (multiverse).. eitherway it does not work... Maybe bacause when I add them in repositories they dont stick that way.. I can add them again and again.. and nothing happens... is there somthing Im doing wrong?

Why do you think that the added repos are not saved? Look at your /etc/apt/sources.list and see if those repos are there and/or post that file here.

It does take some work and reading to get ATI video cards working correctly, but you need to know your card model designation.

To find out what GPU/video card you have open the terminal application and type > lspci -v

---

### Post by aktiwers on 2008-04-21
> **yngvrr said:**
> He.. I didnt see the last message when I wrote my last... Anyway.. I put in this command as suggested : "sudo aptitude update" and a lot of things happened.. then I put in the other one : "sudo aptitute install compizconfig-settings-manager" and this is what happened : 
[SIZE=2]"Reading package lists... Done
 Building dependency tree... Done
 initialising package states... Done
 Building tag database... Done
Couldn't find any package whose name or description matched "compizgonfig-settings-manager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and ö not upgraded.
Need to get OB of archives. Afterunpacking OB will be used."[/SIZE]

Its:
```
sudo aptitude install compizconfig-settings-manager
```

NOT:
```
sudo aptitude install compiz**g**onfig-settings-manager
```

:)

---

### Post by yngvrr on 2008-04-21
hehe... but yeah I did that right... I just did it wrong when copying it in here.. I did that manually because I cant copy-paste...

And Im sorry but I have no clue what youre talking about, phidia.. I did, however, try that command in the terminal but it just says it is invalid...

Im begining to feel extreamly stupid..

---

### Post by SlappyPappy on 2008-04-22
In terminal type

sudo lshw

BTW that is and L.

Then copy what's in the display portion here so people can give you some help.

---

### Post by yngvrr on 2008-04-29
Nothing worked so I installed Ubuntu 8.04 to see if that would help.. However the situation did not improve much... I was able to download the compizconfig-settings-manager and I can open it.. It just does not work something people say is because of my graphic card driver.. And also since I installed 8.04 I cant watch video online.. nothing at all, not even youtube.. although I have downloaded java and flash and gnash nothing workes.. I thought it might be caused by the same problem that I have with the desktop effects.. does that make sence? 

another thing.. Someone was trying to help me in another thread I posted but cant find... he wanted me to do something in ..System/administrator/hardware drivers.. tick something but there is nothing there.. like I have no drivers or something...

Can someone please help I'm getting really desperate.. 

Anyway.. This is what comes when I type sudo lshw : 

" description: Notebook
    product: HP nx9005 (DJ318A)
    vendor: Hewlett-Packard
    version: KAM1.57
    serial: CNF4091B62
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=E02FDEE0-2F63-D811-9C67-000E7F6FF48E
  *-core
       description: Motherboard
       product: 0024
       vendor: Hewlett-Packard
       physical id: 0
       version: PQ1A83
       serial: None
       slot: &#65533;&#65533;&#65533;USB2
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies Ltd.
          physical id: 0
          version: KAM1.57 (02/19/2004)
          size: 110KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom pcmciaboot edd int13floppynec int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp
     *-cpu
          description: CPU
          product: mobile AMD Athlon(tm) XP2400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: mPGA462B
          size: 1788MHz
          capacity: 1795MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts fid vid cpufreq
        *-cache:0
             description: L2 cache
             physical id: 8
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:2
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 512MiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: M2
             size: 256MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: AGP Bridge [IGP 320M]
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 13
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-ati latency=32 module=ati_agp
        *-pci
             description: PCI bridge
             product: PCI Bridge [IGP 320M]
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon Mobility U1
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=66 mingnt=8
        *-usb
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-multimedia
             description: Multimedia audio controller
             product: M5451 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ALI 5451 latency=64 maxlatency=24 mingnt=2 module=snd_ali5451
        *-isa
             description: ISA bridge
             product: M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-communication UNCLAIMED
             description: Modem
             product: M5457 AC'97 Modem Controller
             vendor: ALi Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=64
        *-pcmcia:0
             description: CardBus bridge
             product: OZ6933/711E1 CardBus/SmartCardBus Controller
             vendor: O2 Micro, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
        *-pcmcia:1
             description: CardBus bridge
             product: OZ6933/711E1 CardBus/SmartCardBus Controller
             vendor: O2 Micro, Inc.
             physical id: a.1
             bus info: pci@0000:00:0a.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ALI15x3_IDE latency=32 maxlatency=4 mingnt=2 module=alim15x3
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: SAMSUNG MP0402H
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: YQ200-04
                   serial: S03WJ30L307246
                   size: 37GiB (40GB)
                   capacity: 37GiB (40GB)
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 signature=b311b311 smart=on
                 *-volume:0
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      version: 1.0
                      serial: 3f647ce8-2b21-43bc-9e5d-7eb1619e743e
                      size: 3121MiB
                      capacity: 3121MiB
                      capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                      configuration: filesystem=ext3 modified=2008-04-25 22:34:31 mounted=2008-04-25 22:34:31 state=clean
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 34GiB
                      capacity: 34GiB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume:0
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 1286MiB
                         capabilities: nofs
                    *-logicalvolume:1
                         description: Linux filesystem partition
                         physical id: 6
                         logical name: /dev/hda6
                         logical name: /
                         logical name: /dev/.static/dev
                         capacity: 31GiB
                         configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                    *-logicalvolume:2
                         description: Linux swap / Solaris partition
                         physical id: 7
                         logical name: /dev/hda7
                         capacity: 1286MiB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: SAMSUNG CDRW/DVD SN-324F
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: U201
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                   configuration: status=nodisc
        *-bridge
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge pm
             configuration: driver=ali1535_smbus latency=0 module=i2c_ali1535
        *-network
             description: Ethernet interface
             product: DP83815 (MacPhyter) Ethernet Controller
             vendor: National Semiconductor Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 00
             serial: 00:0e:7f:6f:f4:8e
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.66 latency=90 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=100MB/s"

---

### Post by yngvrr on 2008-04-30
Isnt there anyone who can help me?

---

### Post by persianprez on 2008-05-01
compiz fusion beryl or emerald ^-^ get the cube and expo! everyone i show it to makes em wanna switch from crappy ol vista to ubuntu!

---

