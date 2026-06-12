---
title: "Live CD Won't  Install Completely"
date: 2012-03-07
forum: Apple Hardware Users
---

### Post by Javelin Dan on 2012-03-07
[COLOR=black][FONT=Verdana]I’ve been trying unsuccessfully to install a live CD of the Lubuntu 12.04 Ppc daily build (various dates) on an old G4 “Graphics” model. Originally, I was going to participate in the pre-release testing, but could never get the desktop to come up. It initially boots OK, (I get the Lubuntu splash screen) then the monitor clicks off and on again (normal) and I get a black screen with a cursor that I can move with the mouse (also normal), but the desktop just never comes up. If I insert the same CD in my wife’s G4 eMac, it will boot up completely. I had the same experience trying to install Linux Mint (9) Ppc on this machine. For the record, this *_is_* a particularly cranky machine that I have only been able to boot a small handful of distros on. I’m assuming I have some sort of graphics issue, but don’t have a clue what to do next. Everything I know about this machine is listed below. Any suggestions appreciated[/FONT][/COLOR]
 
 
 
*[COLOR=black][FONT=Verdana]Serial # XA00701SHSF, 450MZ / 1M cache, 128MB, SDRAM 20GB, HD/DVD ROM, zip / 56K, modem / KB.[/FONT][/COLOR]*
 
*[FONT=Verdana][COLOR=black]Intro. Date: August 31, 1999* Disc. Date: July 19, 2000* Order No: M7232LL/A* Model No: M5183 (EMC 1843) Subfamily: Power Mac G4 - AGP Model ID: PowerMac3,1 Std. RAM: 128 MB, 256 MB* Std. VRAM: 16 MB Std. HD: 20, 27 GB (7200 RPM) Std. Optical: 5X DVD-ROM, RAM Complete Power Macintosh G4 450 (AGP) Specs[/COLOR][/FONT]*
 
*[COLOR=black][FONT=Verdana]Hardware Info: [/FONT][/COLOR]*
 
*[FONT=Verdana][COLOR=black]Host bridge – Apple Computer Inc. Uninorth International PCI[/COLOR][/FONT]*
 
*[FONT=Verdana][COLOR=black]PCI bridge – Digital Equipment Corp. DECchip 21154 (Rev 05) (prog-if 00 {Normal decode})[/COLOR][/FONT]*
 
*[FONT=Verdana][COLOR=black]USB Controller(s) – Apple Computer Inc. KeyLargo USB (prog-if 10 {OHCI})[/COLOR][/FONT]*
*[FONT=Verdana][COLOR=black]Apple Computer Inc. KeyLargo USB (prog-if 10 {OHCI})[/COLOR][/FONT]*
 
*[FONT=Verdana][COLOR=black]Storage[/COLOR][/FONT]*
 
*[FONT=Verdana][COLOR=black]Primary Master /dev/hda disk[/COLOR][/FONT]*
*[FONT=Verdana][COLOR=black]Model IBM-DPTA-372050[/COLOR][/FONT]*
*[FONT=Verdana][COLOR=black]Capacity 20 GB[/COLOR][/FONT]*
*[FONT=Verdana][COLOR=black]Cache 1.961 MB[/COLOR][/FONT]*
 
*[FONT=Verdana][COLOR=black]Primary Slave /dev/hdb disk[/COLOR][/FONT]*
*[FONT=Verdana][COLOR=black]Model Maxtor 54089U8[/COLOR][/FONT]*
*[FONT=Verdana][COLOR=black]Capacity 40 GB[/COLOR][/FONT]*
*[FONT=Verdana][COLOR=black]Cache 2.048 MB[/COLOR][/FONT]*
 
*[FONT=Verdana][COLOR=black]Secondary Master /dev/hdc cdrom[/COLOR][/FONT]*
*[FONT=Verdana][COLOR=black]Model MATSHITADVD-ROM SR-8585[/COLOR][/FONT]*
*[FONT=Verdana][COLOR=black]Capacity No Media[/COLOR][/FONT]*
*[FONT=Verdana][COLOR=black]Secondary Slave /dev/hdd Floppy[/COLOR][/FONT]*
*[FONT=Verdana][COLOR=black]Model 10 MEGA Zip 100 ATAPI[/COLOR][/FONT]*

---

### Post by MisterGaribaldi on 2012-03-07
Hmm...

Usually, if everything else installed correctly and you can't get into X.org's GUI environment, that's probably a result of insufficient RAM.

You appear to just have grabbed generic specs information on your Mac and pasted it here. We need to know how much RAM you actually have, and what graphics card you actually have.

Most Macs of that vintage can be upgraded to at least 512MB, if not 1GB of RAM. If you really want to use the thing as a desktop system with Linux, I'd highly recommend you ensure you've got as much RAM in it as you can get.

Also, since you're getting raster (that is to say, you're not just getting a "out of scan-range" or "unsupported resolution" type of error from your monitor) it's not that your graphics card isn't supported. However, it is possible that your card itself may not have enough VRAM on it to fully support a graphical environment. Again, post your specs so we have something to work with.

---

### Post by Javelin Dan on 2012-03-07
I will be more than happy to oblige if you'll just tell me where to get it.

---

### Post by Javelin Dan on 2012-03-07
I should also tell you that I've had Ubuntu 10.10 installed on this machine and it runs very well if not a little slow. Ditto for Debian 6, and an old distro of Xubuntu 6.06 I had laying around. I've also successfully run a live CD of Kubuntu 10.10. All of these (but only these) have run without any graphics issues. I bought this machine used at a garage sale for $20 (US) with no book so I know little about it, but remember seeing somewhere that it now has 506 MB of ram installed. Not stellar, but still should run a basic OS even if a little slow, don't you think?

Another thing comes to mind which may mean something. On several attempts with different daily builds of Lubuntu, if I tried to boot 3 or 4 times, I would eventually get a desktop and all the graphics seemed to run fine until I would reboot and have the same problem over again. Mean anything to you?

---

### Post by westie457 on 2012-03-07
Hi get one of the LiveCDs that you know works. Boot into 'Try' mode and open a terminal (Ctrl+Alt+T) and run ```
lshw
```

Post the entire output here between [code] tags by clicking on the # symbol and pasting in the brackets.

I might be able to help however someone else will.

Thank you.

---

### Post by marinara on 2012-03-07
good luck, i have the black screen thing on one of my pcs.  luckily it has enough ram to run 10.04

---

### Post by Javelin Dan on 2012-03-08
Thanks westie457 - I have a meeting tonight that will get me home late. If I have time I'll post tonight, but if not, tomorrow. Please stay tuned everyone...
 
marinara - Yeah, that's what I don't get. Why enough RAM to run one OS easily but not another? I do get that the "bleeding edge" distros are focusing on newer equipment using newer kernels not necessarily compatible with older stuff, but in the case of Lubuntu, I thought it was supposed to be geared toward older equipment and be "easy" on resources. In my struggles, I've been focussing mainly on distros that are supposed to embrace my older junk. If someone could just explain what's going on, I would be grateful.

---

### Post by Javelin Dan on 2012-03-08
Sorry, I couldn't figure out how to post the way you asked, but here is the info anyway:

ubuntu                    
    description: Computer
    product: PowerMac G4 AGP Graphics
    vendor: Copyright 1983-1999 Apple Computer, Inc. All Rights Reserved
    serial: HSFM7628LL/AXA007015
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
       clock: 99MHz
       capabilities: powermac3_1 macrisc power_macintosh
     *-firmware
          product: OpenFirmware 3
          physical id: 0
          logical name: /proc/device-tree
          capabilities: bootinfo
     *-memory
          description: System memory
          physical id: 1
          size: 512MiB
        *-bank:0
             description: SDRAM
             product: PC100-322S
             physical id: 0
             version: 3043,01 00,01
             serial: M3 66S1623CT0-C1L
             slot: DIMM0/J21
             size: 128MiB
        *-bank:1
             description: SDRAM
             product: PC100-322S
             physical id: 1
             version: 0000,0A 62,52
             serial: GMM26416233CMTG-7J
             slot: DIMM1/J22
             size: 128MiB
        *-bank:2
             description: SDRAM
             product: PC100-322S
             physical id: 2
             version: 0000,0A 62,52
             serial: GMM26416233CMTG-7J
             slot: DIMM2/J23
             size: 128MiB
        *-bank:3
             description: SDRAM
             product: PC100-322S
             physical id: 3
             version: 0000,0A 62,52
             serial: GMM26416233CMTG-7J
             slot: DIMM3/J24
             size: 128MiB
     *-cpu
          description: CPU
          product: 7400, altivec supported
          physical id: 2
          bus info: cpu@0
          version: 2.8 (pvr 000c 0208)
          size: 450MHz
          clock: 99MHz
          capabilities: altivec performance-monitor
        *-cache:0
             description: L1 Cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 Cache (unified)
             physical id: 1
             size: 1MiB
             clock: 225MHz (4.4ns)
     *-pci:0
          description: Host bridge
          product: UniNorth AGP
          vendor: Apple Computer Inc.
          physical id: 100
          bus info: pci@0000:00:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-uninorth latency=16
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Radeon RV250 If [Radeon 9000]
             vendor: ATI Technologies Inc
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=radeonfb latency=255 mingnt=8
             resources: irq:48 memory:98000000-9fffffff ioport:400(size=256) memory:90000000-9000ffff memory:90020000-9003ffff
     *-pci:1
          description: Host bridge
          product: UniNorth PCI
          vendor: Apple Computer Inc.
          physical id: 101
          bus info: pci@0001:10:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=16
        *-pci
             description: PCI bridge
             product: DECchip 21154
             vendor: Digital Equipment Corporation
             physical id: d
             bus info: pci@0001:10:0d.0
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
             resources: memory:80000000-800fffff
           *-generic
                description: Unassigned class
                product: KeyLargo Mac I/O
                vendor: Apple Computer Inc.
                physical id: 7
                bus info: pci@0001:11:07.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=macio latency=16
                resources: irq:0 memory:80000000-8007ffff
              *-ide:0
                   description: IDE Channel 0
                   physical id: 0
                   bus info: ide@0
                   logical name: ide0
                   clock: 33MHz
                 *-disk:0
                      product: IBM-DPTA-372050
                      vendor: IBM
                      physical id: 0
                      bus info: ide@0.0
                      logical name: /dev/hda
                      capacity: 19GiB (20GB)
                 *-disk:1
                      product: Maxtor 54098U8
                      vendor: Maxtor
                      physical id: 1
                      bus info: ide@0.1
                      logical name: /dev/hdb
                      capacity: 38GiB (40GB)
              *-ide:1
                   description: IDE Channel 0
                   physical id: 1
                   bus info: ide@1
                   logical name: ide1
                   clock: 33MHz
                 *-cdrom
                      product: MATSHITADVD-ROM SR-8585
                      physical id: 0
                      bus info: ide@1.0
                      logical name: /dev/hdc
                      logical name: /cdrom
                      capacity: 709MiB (744MB)
                      capabilities: packet
                      configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
                 *-floppy
                      product: IOMEGA ZIP 100 ATAPI
                      physical id: 1
                      bus info: ide@1.1
                      logical name: /dev/hdd
              *-ide:2
                   description: IDE Channel 0
                   physical id: 2
                   bus info: ide@2
                   logical name: ide2
                   clock: 33MHz
           *-usb:0
                description: USB Controller
                product: KeyLargo USB
                vendor: Apple Computer Inc.
                physical id: 8
                bus info: pci@0001:11:08.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master
                configuration: driver=ohci_hcd latency=16 maxlatency=86 mingnt=3
                resources: irq:27 memory:80082000-80082fff
           *-usb:1
                description: USB Controller
                product: KeyLargo USB
                vendor: Apple Computer Inc.
                physical id: 9
                bus info: pci@0001:11:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master
                configuration: driver=ohci_hcd latency=16 maxlatency=86 mingnt=3
                resources: irq:28 memory:80081000-80081fff
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB12LV23 IEEE-1394 Controller
                vendor: Texas Instruments
                physical id: a
                bus info: pci@0001:11:0a.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=16 maxlatency=4 mingnt=2
                resources: irq:63 memory:80080000-800807ff memory:80084000-80087fff
     *-pci:2
          description: Host bridge
          product: UniNorth Internal PCI
          vendor: Apple Computer Inc.
          physical id: 102
          bus info: pci@0002:21:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=16
        *-network
             description: Ethernet interface
             product: UniNorth GMAC (Sun GEM)
             vendor: Apple Computer Inc.
             physical id: f
             bus info: pci@0002:21:0f.0
             logical name: eth0
             version: 00
             serial: 00:30:65:55:a8:ca
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master rom ethernet physical
             configuration: broadcast=yes driver=sungem driverversion=0.98 ip=192.168.2.100 latency=16 maxlatency=64 mingnt=64 multicast=yes
             resources: irq:41 memory:f5200000-f53fffff memory:f5000000-f50fffff
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ root
No command 'root' found, did you mean:
 Command 'rbot' from package 'rbot' (universe)
root: command not found
ubuntu@ubuntu:~$

---

### Post by marinara on 2012-03-09
you need 400 mb of ram to run the live cd.
if you download the alternate installer, you can install and run lubuntu on 128mb of ram

---

### Post by Javelin Dan on 2012-06-05
Just ran across this and thought I'd update it several months later. It was the RAM. I installed a 512 MB card for a total of 890 MB and everything booted and ran, although a little slower than I would like. I just added more memory and brought the total up to 1152 MB of RAM and it runs much better. I would just like to figure out why this box needs so much RAM to run normally...

---

