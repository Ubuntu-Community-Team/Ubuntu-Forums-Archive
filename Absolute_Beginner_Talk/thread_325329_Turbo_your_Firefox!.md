---
title: "Turbo your Firefox!"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-12-25
Hi everyone,

I've seen this discussed on the site but, as far as I can tell, it was over a year ago. 

My FF's OK; I tweaked it in many ways but, but, but...
I tried something I remembered from Windows but I was convinced that it wouldn't work under Linux. It does and, as far as I can tell, the difference in browsing speed is amazing on my box. As I said previously, this is not the only tweaking I did!
Type:
```
about:config
```

You'll probably need to create:
Right click in *about:config* > *Boolean* and C/P the following in the dialog box:
> browser.turbo.enabled 
Then just OK!

And here click to make it "true".
The whole line should look like this:
> browser.turbo.enabled   user set   boolean   true
Restart Fox!

---

### Post by H.E. Pennypacker on 2006-12-25
Mind explaining how this works, and why it speeds things up?

---

### Post by kerry_s on 2006-12-25
Thats a windows option, but it is no longer used->

browser. turbo. enabled 	 Boolean 	 Pref removed (obsolete). Previously:
Determined whether to load browser in "Turbo Mode" (aka "quick launch") (Windows/Mozilla Suite only)
True: Load some Mozilla code into memory on Windows boot
False (default): Load browser normally on program execution

If you want to play with about:conf here's the list of options->

google "http://kb.mozillazine.org/Firefox_:_FAQs_:_About:config_Entries"

The page can't be linked.

---

### Post by xyz on 2006-12-25
I guess I didn't make myself clear. Sorry about that. As I said:
> I tried something I remembered from Windows but I was convinced that it wouldn't work under Linux.
I realized it's not supposed to work for Linux; Google says so; everybody says so and even I said so.
I just decided to give it a try and it works for me. I'm extremely surprised at the difference it's made for me;esp. since as stated above, everybody says it doesn't work. That's all!

As we've all witnessed on these forums, lots of things *depend* on your specs, HW, various tweakings and so on.
I just thought I'll passed it on...it's up to you...as always!
>  **description**: Notebook
    product: Satellite A40
    vendor: TOSHIBA
    version: PSA40E-0DEWN-S4
    serial: 54039386H
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3

 ***-core**
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA

 ***-firmware**
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.50 (01/26/2004)
          size: 128KB
          capacity: 448KB

 ***-cpu**
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.70GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: uFC-PGA Socket
          size: 2700MHz
          capacity: 2700MHz
          width: 32 bits
          clock: 100MHz

 ***-memory**
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 512MB
          capacity: 2GB

  ***-pci**
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation



---

### Post by k1001001 on 2006-12-25
A bit off-topic, but how did you get the information about your PC to display like that? I assume it's a terminal command similar to lshw, but I can't think of it at the moment.

How does it really browse faster? Does it download faster? The only way I really know it could work would be to cache frequently-accessed pages, but that's never really done much good for me.

---

### Post by LameBMX on 2006-12-25
it opens up faster ... because a good chunk of it stays resident in ram until you actually request the program ... and that feature is still in the windows version .. kinda hidden with advanced options or somewhere ... it doesnt really make browsing any faster just makes FF open up faster ... now it kinda could work in *nix .. while nix keeps ram full and leaves things cached ... it could keep it open in ram so it dont get over written by another program thus speeding up a launch after running a bunch of things ... oh and in the windows version it had an icon in the task bar for it :)

---

### Post by kerry_s on 2006-12-25
> **xyz said:**
> I guess I didn't make myself clear. Sorry about that. As I said:

I realized it's not supposed to work for Linux; Google says so; everybody says so and even I said so.
I just decided to give it a try and it works for me. I'm extremely surprised at the difference it's made for me;esp. since as stated above, everybody says it doesn't work. That's all!

As we've all witnessed on these forums, lots of things *depend* on your specs, HW, various tweakings and so on.
I just thought I'll passed it on...it's up to you...as always!


What ubuntu version? Firefox version?

---

### Post by k1001001 on 2006-12-25
> **LameBMX said:**
> it opens up faster ... because a good chunk of it stays resident in ram until you actually request the program ... and that feature is still in the windows version .. kinda hidden with advanced options or somewhere ... it doesnt really make browsing any faster just makes FF open up faster ... now it kinda could work in *nix .. while nix keeps ram full and leaves things cached ... it could keep it open in ram so it dont get over written by another program thus speeding up a launch after running a bunch of things ... oh and in the windows version it had an icon in the task bar for it :)
I see. It caches Firefox in the RAM. Not my cup of tea since FF usually opens in under 2 seconds on my computer, but I suppose it would be more useful on computers with more limited resources. I used to have a Packard Bell running Win98 that took the same amount of time to dial up to an ISP as it did to open Firefox (about 30-45 seconds). Those were the days...

---

### Post by riven0 on 2006-12-25
> **k1001001 said:**
> A bit off-topic, but how did you get the information about your PC to display like that? I assume it's a terminal command similar to lshw, but I can't think of it at the moment.

How does it really browse faster? Does it download faster? The only way I really know it could work would be to cache frequently-accessed pages, but that's never really done much good for me.

Yeah, how did you get that? Was it **lshw -businfo**?

---

### Post by xyz on 2006-12-26
Thanks folks for the technical explanations on why/how it is faster!
*If I understood you right, I'm not actually browsing/surfing faster; it's just that FF opens up faster?*

Can it in any way be _bad_?...cause hw problems or anything else?

Well, once the how/why's explained, I'm still moving much faster. As you can see below, I don't have an extremely fast box; however, I'm also far from running a Ford-T!
Whether I start FF, click on a link, Google, change Tabs - even my Gmail opens up way before the water boils - speed increase is a *reality* regardless of how it was achieved.

Here is the entire output of:
> root@luser:~# lshw
luser
    **description**: Notebook
    product: Satellite A40
    vendor: TOSHIBA
    version: PSA40E-0DEWN-S4
    serial: 54039386H
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=enabled boot=normal chassis=notebook frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=D905B200-A242-11D8-80D1-C55454039386
  

***-core**
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: $$C0458A20
    

** *-firmware**
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.50 (01/26/2004)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp upgrade shadowing vesa cdboot bootselect pcmciaboot edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot
     

***-cpu**
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.70GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: uFC-PGA Socket
          size: 2700MHz
          capacity: 2700MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr cpufreq
          configuration: id=0
       

** *-cache**:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 8KB
             capacity: 8KB
             clock: 1GHz (1ns)
             capabilities: internal write-back data
        

***-cache**:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 128KB
             capacity: 128KB
             clock: 1GHz (1ns)
             capabilities: internal write-back
    

** *-memory**
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 512MB
          capacity: 2GB
        

***-bank**:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 0
             size: 256MB
             width: 64 bits
        

***-bank**:1
             description: SODIMM SDRAM Synchronous
             physical id: 1
             slot: DIMM 1
             size: 256MB
             width: 64 bits
     

***-pci**
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        

***-system**:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
        

***-system**:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
        

***-display**:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 02
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:d8000000-dfffffff iomemory:d0000000-d007ffff ioport:eff8-efff irq:10
        

***-display**:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 02
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:20000000-27ffffff iomemory:2a000000-2a07ffff
       

** *-usb**:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1000-101f irq:185
           

***-usbhost**
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-686 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              

***-usb**
                   description: Mouse
                   product: Optical Wheel Mouse
                   vendor: Dell Computer Corp.
                   physical id: 2
                   bus info: usb@1:2
                   version: 2.20
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        

***-usb**:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1020-103f irq:193
           

***-usbhost**
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-686 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
       

** *-usb**:2
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:cffffc00-cfffffff irq:201
           

***-usbhost**
                product: EHCI Host Controller
                vendor: Linux 2.6.15-27-686 ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
       

** *-pci**
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           

***-network**
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@01:08.0
                logical name: eth0
                version: 83
                serial: 00:08:0d:fe:f6:f6
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.14-k4-NAPI duplex=full firmware=N/A ip=84.74.181.101 link=yes multicast=yes port=MII speed=100MB/s
                resources: iomemory:cfeff000-cfefffff ioport:cf40-cf7f irq:209
           

***-pcmcia**
                description: CardBus bridge
                product: ToPIC100 PCI to Cardbus Bridge with ZV Support
                vendor: Toshiba America Info Systems
                physical id: b
                bus info: pci@01:0b.0
                version: 33
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:cfe00000-cfe00fff irq:169
       

***-isa** UNCLAIMED
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        

***-ide**
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:bfa0-bfaf iomemory:2a080000-2a0803ff irq:169
           

***-ide**:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              

***-disk**
                   description: ATA Disk
                   product: HTS541080G9AT00
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: MB4OA60A
                   serial: MP28MBXBGMYAUH
                   size: 74GB
                   capacity: 74GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 

***-volume**:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 14GB
                      capabilities: primary bootable
                 
***-volume**:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 10001MB
                      capabilities: primary
                 

***-volume**:2
                      description: W95 FAT32 (LBA) partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 48GB
                      capabilities: primary
                 

***-volume**:3
                      description: W95 Ext'd (LBA) partition
                      physical id: 4
                      bus info: ide@0.0,4
                      logical name: /dev/hda4
                      capacity: 1419MB
                      capabilities: primary
           

***-ide**:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              

***-cdrom**
                   description: DVD reader
                   product: TOSHIBA DVD-ROM SD-R2412
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1431
                   serial: 444J306314
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                   configuration: mode=udma2
                 

***-disc**
                      physical id: 0
                      logical name: /dev/hdc
        

***-serial** UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             resources: ioport:d880-d89f
        

***-multimedia**
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:be00-beff ioport:bdc0-bdff iomemory:cfdffe00-cfdfffff iomemory:cfdffd00-cfdffdff irq:177
        

***-communication** UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             resources: ioport:ba00-baff ioport:b980-b9ff irq:177


---

### Post by STREETURCHINE on 2006-12-26
well i have to say i tried your turbo charge,
have now turned it off as my internet browsing slowed to a crawl pages opened so slow i made a coffee and still had to wait some.
as soon as i turned it off every thing went back to normal ,
and my specs 
intel pentium 4 ',3.00 ghz processer. 1 gig sdram, so on and so forth

---

### Post by xyz on 2006-12-26
> **STREETURCHINE said:**
> well i have to say i tried your turbo charge,
have now turned it off as my internet browsing slowed to a crawl pages opened so slow i made a coffee and still had to wait some.
as soon as i turned it off every thing went back to normal ,
and my specs 
intel pentium 4 ',3.00 ghz processer. 1 gig sdram, so on and so forth

Thanks for trying/posting...one of the thread's points being to try to determine for whom it is a good/bad/useless thing! Based on people posting their RAM, processor and so on.

---

