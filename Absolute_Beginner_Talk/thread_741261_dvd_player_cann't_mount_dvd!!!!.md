---
title: "dvd player cann't mount dvd!!!!"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by d1234 on 2008-03-31
my dvd player only mounts cd but not dvd!!!! the moment i insert dvd it says "can not mount volume-- invalid mount option when attempting to mount the volume" please help me out!!!!!

---

### Post by Michael.Godawski on 2008-03-31
Can you please post the output of these commands to identify your dvd player?

```
lspci

sudo lshw 
```

Did you manage to play dvds in the past or since are these issues occurring since the very beginning?

---

### Post by d1234 on 2008-04-01
>  description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=00AC19BA-9C7A-DA11-9706-0018F35FB8CC
  *-core
       description: Motherboard
       product: M2NPV-MX
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 1.xx
       serial: 123456789000
       slot: L1 Cache
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS M2NPV-MX ACPI BIOS Revision 0405 (08/25/2006)
          size: 128KB
          capacity: 448KB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.11.2
          slot: Socket AM2
          size: 2200MHz
          capacity: 3700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc
        *-cache:0
             description: L1 cache
             physical id: b
             slot: L1 Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: d
             slot: L2 Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous internal write-back unified
     *-cpu:1
          description: CPU
          vendor: AMD
          physical id: 4
          bus info: cpu@1
          version: 15.11.2
          slot: Socket AM2
          size: 2200MHz
          capacity: 3700MHz
          clock: 200MHz
        *-cache:0
             description: L1 cache
             physical id: c
             slot: L1 Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: e
             slot: L2 Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 33
          slot: System board or motherboard
          size: 512MB
        *-bank:0
             description: DIMM 667 MHz (1.5 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             width: 64 bits
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: C51PV [GeForce 6150]
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga bus_master cap_list
          configuration: driver=nvidia latency=0 module=nvidia
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3 module=amd74xx
        *-ide
             description: IDE Channel 1
             physical id: 1
             bus info: ide@1
             logical name: ide1
             clock: 66MHz
           *-cdrom
                description: DVD writer
                product: SONY DVD RW AW-Q170A
                physical id: 0
                bus info: ide@1.0
                logical name: /dev/hdc
                version: 1.70
                capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                configuration: mode=udma4 status=nodisc
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          logical name: scsi0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: SCSI Disk
             product: ST380215AS
             vendor: ATA
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: 6QZ08FRT
             size: 74GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
           *-volume:0
                description: HPFS/NTFS partition
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                capacity: 18GB
                capabilities: primary bootable
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 38GB
                capacity: 38GB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: W95 FAT32 partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 18GB
              *-logicalvolume:1
                   description: HPFS/NTFS partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 18GB
              *-logicalvolume:2
                   description: Linux swap / Solaris partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 839MB
                   capabilities: nofs
           *-volume:2
                description: Linux filesystem partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                capacity: 17GB
                capabilities: primary
     *-ide:2
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:3
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 00:18:f3:5f:b8:cc
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=192.168.1.5 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp


this is what revealed when i put the command in terminal..... and this problem i'm facing since i installed ubuntu.....thanks for your earlier reply.... and looking forward for your cooperation again!!!!!!!!!!!!!!!!!!!!!!!!!!!1

---

### Post by d1234 on 2008-04-01
please help!!!!!!!!!!!!!!!!!!!!

---

### Post by d1234 on 2008-04-03
help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Astinsan on 2008-04-03
Hello D1234

I have had this bug happen to me and found there is a solution. Remember that Ubuntu 7 is not a final draft and there is going to be bugs. 

Since this is in the new to ubuntu section I will give you a quick answer with a step by step fix.

This is the Post that has the same issue. 
[http://ubuntuforums.org/showthread.php?t=195403](http://ubuntuforums.org/showthread.php?t=195403)

There is a Bug with fstab and the mounting system
> 
Quote:
Originally Posted by sopo_dan
LOL, this is freaky!
I've done some more reading through the man page for mount, but haven't gotten any smarter out of it, so I thought I'd try "experimenting"
So, as i stated in the original post, my /etc/fstab line used to read:
Code:

 /dev/hda        /media/cdrom0       udf,iso9660 user,noauto     0       0

I changed it to:
Code:

 /dev/hda        /media/cdrom0       iso9660,udf user,noauto     0       0

and now both fs types work fine (pop in the disk and it gets mounted)


Now before we go into the fix bring up a terminal and look at the configuration file in read only mode.

The terminal is located by default in the Applications menu under Accessories. (Terminal should be in there)


Once you are at the prompt  (username@computername:)

type gedit /etc/fstab

According to your device print out your dvd writer / reader is device /dev/hdc. Look for that device line. 
See if it lists the cdrom mount with udf first. If it does close gedit and we will edit it for real.  

In the terminal type sudo gedit /etc/fstab

It will prompt you for a password. The password is the same as your user login password you chose during the install. 


Go back to the device line /dev/hdc

Change the mount options so that  iso9660 is in front of udf . Click the save button on gedit close everything and reboot.

If the disk magically mounts with out a problem enjoy.

---

### Post by d1234 on 2008-04-07
this is what i got after placing the command "gedit / etc / fstab" in the terminal.... now please tell me where i exactly make the change to get my dvd player working.....!!!!!!



```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=43b2e338-f50e-4147-afc0-8c9ec8c99198 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=c4c0afe0-c63a-4eb3-a120-bf12db9352fe none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf, iso9660 user, noauto,exec 0       0
```

---

### Post by d1234 on 2008-04-08
please help!!!!!!!

---

### Post by d1234 on 2008-04-08
help!!! help!!! help please.....................

---

### Post by stchman on 2008-04-08
> **d1234 said:**
> my dvd player only mounts cd but not dvd!!!! the moment i insert dvd it says "can not mount volume-- invalid mount option when attempting to mount the volume" please help me out!!!!!

I have had this happen to me before.  Are these data DVDs?  Can you play video DVDs?  If you burn a data DVD in Windows using the Windows filesystem then you can have problems.  I simply re-burn the data DVD in a pure iso9660 format and all is well.

Got to love M$ proprietary stuff.

---

### Post by Astinsan on 2008-04-10
> /dev/hdc        /media/cdrom0   udf, iso9660 user, noauto,exec 0       0

flip udf, iso9660 to read iso9660, udf

> /dev/hdc        /media/cdrom0   iso9660, udf user, noauto,exec 0       0

That is what fixed it for me.

---

### Post by d1234 on 2008-04-14
done everything as per the instructions given in different posts........but still facing the problem....... and also my cd\dvd drive is not ejecting(since i installed ubuntu) when the "eject" command is given it shows "unable to mount the volume ..... there is no media in the drive" however i can manually open the drive for playing cd... but it could not mount dvd...... please help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by d1234 on 2008-04-15
is there anybody who can hep me out?????????????????????????//

---

### Post by d1234 on 2008-04-15
help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Dive4Life on 2008-04-16
I think this may have to do with APIC.  I'm experiencing the same problem that you are.  I, thank God, do not have Windows installed.  But after I upgraded my motherboard I have been experiencing these issues.  Try running some Searches on APIC and see what you come up with. 

P.S.  I have yet to find a fix from any post regarding this issue.

---

### Post by diabolustheslayer on 2008-04-18
All the DVD's and CD's (both music and documents)  I recorded in windows can't be opened in ubuntu, I'm totally new in linux, so please give me an answer for dummies. The DVD works great, i have no problems opening the ones i recorded with ubuntu, i have no problems writing neither, or playing dvd movies. maybe my mistake was totally erasing windows from my computer when i installed ubuntu, does it have anything to do?

---

### Post by Saturn357 on 2008-04-18
Yeah, I can't open the one DVD that I burned in Windows either. I recently just erased Windows and install Ubuntu. It's not that bad though, it was a test CD, and I didn't keep Windows long enough to have anything really important on there. Other than that, everything is working out great. 

They said that if you try to run something you burned on Windows, you would have problems. It's not just because you got rid of Windows, however.

---

