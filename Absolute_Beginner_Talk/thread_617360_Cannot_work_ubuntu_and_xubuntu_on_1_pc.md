---
title: "Cannot work ubuntu and xubuntu on 1 pc"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by sponsoredwalk on 2007-11-19
--------------------------------------------------------------------------------

Hello i am using ubuntu 6.06 with 256ram and yesterday after many arduous and time consuming tries i downloaded the xubuntu 7.10 alternate iso (the many downloads beforehand had problems...md5\defect cd...) to burn and put on my newly purchased second 400g hard drive. I cannot access or mount the drive through ubuntu 6.06 although it shows up in 'computer' and cannot enable or format it using gnome partition editor. So i tried to put xubuntu on my new 400g hard drive clean from ubuntu (ubuntu 6.06 is on my 40g maxed out master drive - 900mb free!!!) and it installed fine. however the last question asked to install on grub and said it should be fine with the listed OS' (it listed ubuntu 6.06) and i clicked ok. then on rebooting i got error 21 and neither OS' loaded. I put in my old ubuntu 6.06 disc and chanced reinstalling the grub menu which , thankfully, worked but there is no sign of xubuntu and when i load up from my slave drive i get error 21, my only idea would be to download the normal xubuntu 7.10 (not alternate) and, manually removing my 40g drive to allow the new 400g drive to be used, install xubuntu onto that. would there be a grub problem in that it would remove 6.06 or is there some way to fix the existing xubuntu? if its any help

sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664832 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 4772 38331058+ 83 Linux
/dev/hda2 4773 4865 747022+ 5 Extended
/dev/hda5 4773 4865 746991 82 Linux swap / Solaris

Disk /dev/hdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 48548 389961778+ 83 Linux
/dev/hdb2 48549 48641 747022+ 5 Extended
/dev/hdb5 48549 48641 746991 82 Linux swap / Solaris

---

### Post by ugm6hr on 2007-11-19
Before going any further - decide what you want your final setup to look like...

Are you planning to erase Ubuntu6.06?  Or do you want to dual-boot 6.06 and 7.10?

I suspect that the issue is with GRUB, but am not certain.  Best to let us see menu.lst

Also - is it OK to have 2 swap partitions?  I don't know the answer to this - but I can imagine it is confusing to have a swap partition on both hard drives.

The only other thing I can say is that I ended up downloading Ubuntu7.10, rather than Xubuntu7.10, because there were always errors on all the Xubuntu downloads.  I think I like Gnome now, anyway.

---

### Post by sponsoredwalk on 2007-11-19
Hey thanx for the speedy reply well i am downloading the ubuntu alternate 7.10 cd to try that but im worried about my 256 ram, thats why i tried xubuntu, well yes the problem is with grub, i was lucky i reinstalled my 6.06 grub, thats fine but its like xubuntu is non existent on my pc, i want to keep both OS' but if i cant sort this out i may just install ubuntu 7.10 completely on its own, i wanted to copy my 30gb of music etc straight onto my new drive but ill have to put them on seperate dvds and just copy those files onto my new OS,

---

### Post by ugm6hr on 2007-11-19
> So i tried to put xubuntu on my new 400g hard drive clean from ubuntu (ubuntu 6.06 is on my 40g maxed out master drive - 900mb free!!!) and it installed fine.

I don't understand what you did.  I am assuming you already had Ubuntu6.06 on the 40G HD, and that you booted from the Xubuntu7.10 AlternateCD to install Xubuntu7.10 on the new 400GB HD.

If that's the case, then I suspect Xubuntu has installed, and you just need to point your GRUB menu.lst to find it.

So - boot 6.06, and paste /boot/grub/menu.lst here (in a "Code" window) - just the bottom half is OK (below where all the lines start with ##).

If you can manually point GRUB to Xubuntu, you can maintain both OS's.

EDIT:
If you are primarily going to be using 7.10, it may be better to use that HD as primary boot device.  Perhaps try going into BIOS at startup, and swapping the boot order (400GB 1st, 40GB 2nd), and then allow it to boot.  That might just work.

---

### Post by natehatewindows on 2007-11-19
why dont you just make a ext3 partition so you can share them with both os's?

---

### Post by ugm6hr on 2007-11-19
> **natehatewindows said:**
> why dont you just make a ext3 partition so you can share them with both os's?

Eh? Both OS's are Linux - so they are ext3 already.  I don't get your point.  How would that help him/her boot?

---

### Post by sponsoredwalk on 2007-11-19
i assume by a code window you mean open up terminal and paste /boot/grub/menu.lst into it, well ill try that but i dont know how to manually point grub to it (soz i am no expert!) I tried switching the boot order and on both drives i got error 21, so i reinstalled my 6.06 grub to my primary drive (40gb) but when i boot from my slave (400g) i get the error, also i dont know what a ext3 partition is or how to do it. thanx

---

### Post by ugm6hr on 2007-11-19
> **sponsoredwalk said:**
> i assume by a code window you mean open up terminal and paste /boot/grub/menu.lst into it, well ill try that but i dont know how to manually point grub to it (soz i am no expert!)

Ok - baby steps:
Boot 6.06
Open /boot/grub/menu.lst
Copy all the text starting with the line that says something like "## ## End Default Options ##"
Reply to this post
Click on the "#" symbol in the Message window that says "Wrap [CODE] tags...." when you move the mouse over it.
Paste the text in the Message window.
Submit reply.

---

### Post by ugm6hr on 2007-11-19
> **sponsoredwalk said:**
> when i boot from my slave (400g) i get the error

When you boot from the 400GB drive, what are the boot options in GRUB?  Which one's give you an error21?  Have you tried all of them?

When you boot from 400GB - there should be an option:
Xubuntu 7.10, kernel 2.6.22-14-generic (or something similar)

If you press "e" (for Edit) when this is highlighted, it should read something like:
```
title		Xubuntu 7.10, kernel 2.6.22-14-generic
root		**(hd0,0)**
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ba004445-16d1-44a7-ab4d-12a1249b6fe0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

The problem will be the bit that is in **bold**.  It should probably read (hd1,0) in your setup.  GRUB allows you to temporarily edit this setting (Using "e" and the keyboard, and then press "b" to retry booting).
This will not do any permanent changes to GRUB - so you may as well try (hd0,0) and (hd1,0) to see which (if any) works.

---

### Post by sponsoredwalk on 2007-11-19
ill post the /boot/grub/menu.lst asap (30mins, im not on my pc!) when i boot from the 400gb drive it loads grub for a millisecond and then i get error 21, i cant do anything after that, the installation was fine so i know its there but i cant touch it.

---

### Post by ugm6hr on 2007-11-19
> **sponsoredwalk said:**
> when i boot from the 400gb drive it loads grub for a millisecond and then i get error 21, i cant do anything after that, the installation was fine so i know its there but i cant touch it.

If you press any key (e.g. down-arrow) during the millisecond that grub is loading, it should interrupt the boot sequence and allow you to select an option (as per previous post).

---

### Post by sponsoredwalk on 2007-11-19
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-29-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-server root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-server
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-server (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-server root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-server
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
i cant even access a menu like this when i try the 400gb disc

---

### Post by ugm6hr on 2007-11-19
Ok - do u know how to edit menu.lst?
```
gksudo gedit /boot/grub/menu.lst
```

Below "### END DEBIAN AUTOMAGIC KERNELS LIST" - we'll try and add an entry for Xubuntu7.04:

```
title		Xubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

That might just work, so you could just try it like that.  Add that to the bottom, and try rebooting (and select that option).  Keep your fingers crossed....

However, I am not certain about what the kernel and initrd file names and paths should be with a different HD..  If it doesn't work: from 6.06, can you find the 7.10 kernal & initrd files?

---

### Post by sponsoredwalk on 2007-11-19
Didn't work, ubuntu 6.06 didn't automatically load, i got a blank screen so i pressed Esc, it brought me to to choose the newly added xubuntu and i got this
Booting Xubuntu 7.10, kernel 2.6.22-14-generic
root (hd1,0)
filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.22-14-generic root=dev/hdb1 ro quiet splash

Error 18 Selected cylinder exceeds maximum supported by bios
HELP!!!:-(

---

### Post by ugm6hr on 2007-11-19
> **sponsoredwalk said:**
> Error 18 Selected cylinder exceeds maximum supported by bios
HELP!!!:-(

I have never encountered this before.  If the location (i.e. hd1,0) was wrong, it should still not give that error.

I don't want to lead you down the garden path without being sure what's going on.  I do have some ideas that are worth pondering:

It mentions that the filesystem is ext2fs - I think there is an upper size limit for ext2fs (which doesn't apply to ext3fs), which may be why it's not working.  Do you remember which you used?

The error about the BIOS is concerning - it seems to suggest that your BIOS (i.e. computer boot software - independent of OS & HD) won't cope with a HD partition of that size.  Don't know what to make of that.  Is your BIOS up-to-date?  Worth checking your computer motherboard manufacturer's website to see if an update is available.

Honestly - now that 6.06 is working OK, it may be easiest to start again with Xubuntu installation from scratch.  It will probably be quicker than this.  The question is how to avoid the same problem.  The best option is perhaps to reformat the new HD, and when installing, create a smaller partition for "/" to see if that works.  But I really am just guessing at this stage.

Sorry.

---

### Post by sponsoredwalk on 2007-11-19
have no idea, think i need to update bios but have no floppy, no idea where to download from, am generally scared, cannot even acces or mount big drive through 6.06 (all i'd really like to do now:-(,) can you or anybody give me (in baby steps:-) ) how to fix this problem it is making ubuntu unbearable...
lshw
description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 255MB
     *-cpu
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.6
          size: 1GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci
          description: Host bridge
          product: 82815 815 Chipset Host Bridge and Memory Controller Hub
          vendor: Intel Corporation
          physical id: e4000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e4000000-e7ffffff
        *-pci:0
             description: PCI bridge
             product: 82815 815 Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV15 [GeForce2 GTS/Pro]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a3
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:d6000000-d6ffffff iomemory:d8000000-dfffffff irq:11
        *-pci:1
             description: PCI bridge
             product: 82801AA PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-usb
                description: USB Controller
                product: USB 2.0 Controller
                vendor: ALi Corporation
                physical id: 9
                bus info: pci@02:09.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: ehci bus_master cap_list
                configuration: driver=ehci_hcd
                resources: iomemory:d5800000-d58000ff irq:9
              *-usbhost
                   product: EHCI Host Controller
                   vendor: Linux 2.6.15-29-386 ehci_hcd
                   physical id: 1
                   bus info: usb@2
                   logical name: usb2
                   version: 2.06
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax/Voice Modem
                vendor: Rockwell International
                physical id: a
                bus info: pci@02:0a.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:d5000000-d500ffff irq:255
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB12LV26 IEEE-1394 Controller (Link)
                vendor: Texas Instruments
                physical id: b
                bus info: pci@02:0b.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:d4800000-d48007ff iomemory:d4000000-d4003fff irq:9
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: d
                bus info: pci@02:0d.0
                logical name: eth0
                version: 10
                serial: 00:e0:18:cf:0b:2b
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too ip=85.134.170.20 multicast=yes
                resources: ioport:d400-d4ff iomemory:d3800000-d38000ff irq:9
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801AA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801AA IDE
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:b800-b80f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   product: ST340823A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 37GB
              *-disk:1
                   product: Hitachi HDT725040VLAT80
                   vendor: Hitachi
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   capacity: 372GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   product: LITE-ON DVDRW SHW-1635S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
              *-cdrom:1
                   product: TOSHIBA DVD-ROM SD-M1502
                   vendor: Toshiba
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capabilities: packet
        *-usb
             description: USB Controller
             product: 82801AA USB
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:b400-b41f irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-29-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Mouse
                   product: Microsoft 3-Button Mouse with IntelliEye(TM)
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@1:1
                   version: 3.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
              *-usb:1
                   description: USB hub
                   product: Generic USB Hub
                   vendor: ALCOR
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=100mA slots=4 speed=12.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: 82801AA SMBus
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             resources: ioport:e800-e80f irq:9
        *-multimedia
             description: Multimedia audio controller
             product: 82801AA AC'97 Audio
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH
             resources: ioport:e000-e0ff ioport:e100-e13f irq:9

---

### Post by ugm6hr on 2007-11-19
> **sponsoredwalk said:**
> cannot even acces or mount big drive through 6.06 (all i'd really like to do now:-(,) can you or anybody give me (in baby steps:-) ) how to fix this problem it is making ubuntu unbearable...

Sorry - I missed that you can't mount the partition in 6.06.

This suggests there is a problem with the HD partition itself.  I would suggest you reformat the HD with GParted (LiveCD), and start again.  Make sure you use ext3fs as the file system. I haven't installed using the AlternateCD before, so am not sure what the options are.

---

### Post by sponsoredwalk on 2007-11-19
i downloaded the ubuntu 7.10 alternate cd and installed it via the disk which went fine, i made the partition smaller - 80gb and when it came to the end (setting up the grub) i chose 1,0 as the boot point and finished, when i started up again i got error 17. i checked and i think i overlapped it with xubuntu which is dormant on the disc, i am going to retry the ubuntu alternate 7.10 installation and format the entire disc via the iso cd, its all i can think of other than upgrading my grub system via a download to cd (not floppy) but have no idea where to go or what to do, is there any chance you could help me find out what do do (based on the lshw info i gave) ? would updating grub mean i could use the entire 400gb disc with ubuntu 7.10? thanks so so much!!!

---

### Post by ugm6hr on 2007-11-19
> **sponsoredwalk said:**
> i downloaded the ubuntu 7.10 alternate cd and installed it via the disk which went fine, i made the partition smaller - 80gb and when it came to the end (setting up the grub) i chose 1,0 as the boot point and finished, when i started up again i got error 17. i checked and i think i overlapped it with xubuntu which is dormant on the disc, i am going to retry the ubuntu alternate 7.10 installation and format the entire disc via the iso cd, its all i can think of other than upgrading my grub system via a download to cd (not floppy) but have no idea where to go or what to do, is there any chance you could help me find out what do do (based on the lshw info i gave) ? would updating grub mean i could use the entire 400gb disc with ubuntu 7.10? thanks so so much!!!

It is hard to know where to start.... The first thing to do is check that the CD you have does not have any errors on it.  I was assuming that had been done.

You should be able to use the full 400GB as a single partition if you use ext3fs file system.  Although the error comment re: BIOS still confuses me - I am uncertain what that has to do with the HD size.

I don't think that lshw helps.  It has nothing to do with your hardware - only possibly the BIOS.  The way to check is to physically remove the 4oGB drive and install (X)Ubuntu as a single only partition on the 400GB drive.  If it works - then you know that this is possible.  You should subsequently be able to reinstall the 40GB drive, edit the NEW grub (on 400GB HD) to allow 6.06 to boot.

But I think it is important you start with a fresh 400GB drive - cos I'm uncertain what has happened to it up to this point.  So use GParted (either from 6.06 or as LiveCD) to reformat it, and then delete all the partitions.  ActiveKillDIsk is a more reliable way to ensure that all the old partitions are destroyed... Just be careful which HD you wipe!

---

### Post by sponsoredwalk on 2007-11-19
i got error 18 after installing 7.10, but it was with my 40gb drive in, what im worried about is that everything in ubuntu 6.06 is read from /dev/hda and if i install 7.10 on the 400g disc when its alone on the pc it will take /dev/hda and when i put the 40gb into /dev/hdb 6.06 will not work. will it? is it a just a ridiculous idea. do i need to upgrade grub? i partitioned 60gb and i get the same problem when i try to mount it, it says its not a removable device, i go to disks manager and Partition 1 is inaccessable and will not enable when i click it. The access path says none and device says  /dev/hdb1

---

### Post by ugm6hr on 2007-11-19
> **sponsoredwalk said:**
> i got error 18 after installing 7.10, but it was with my 40gb drive in, what im worried about is that everything in ubuntu 6.06 is read from /dev/hda and if i install 7.10 on the 400g disc when its alone on the pc it will take /dev/hda and when i put the 40gb into /dev/hdb 6.06 will not work. will it? is it a just a ridiculous idea. do i need to upgrade grub? i partitioned 60gb and i get the same problem when i try to mount it, it says its not a removable device, i go to disks manager and Partition 1 is inaccessable and will not enable when i click it. The access path says none and device says  /dev/hdb1

This sounds like there may be a HD issue here, if you can't create a small-ish ext3fs partition that can be recognised by 6.06.  Have you tried running a HD diagnostic to ensure there is no hardware fault with the new drive?  Just go to the HD manufacturers website and look for a diagnostic CD / floppy image - or try this [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

As for the hda / hdb issue - I don't know if it matters.  If you boot from the 6.06 partition, it will make "/" (root partition) whatever you tell it in the new GRUB menu.lst.  Maybe someone else can clarify this.

---

### Post by sponsoredwalk on 2007-11-20
Took out my 40gb drive, installed ubuntu 6.06 on the 400gb drive, went fine and when it booted up i got error 18, i think i could either update my bios ( but i do not know how to do it i.e. do not know what to download as i dont know the name of my system {pentium 3???} ) or i could install a 32mb partition at the start of the disc (but i dont know, do i have to first wipe the drive clean of 6.06, then create a logical or primary 32 mb partition on ext2, then use the rest of the disc as free space or what do i do with it?) i could really use detailed help i really think its possible to fix this problem and it would be a tribute to linux to get an imbeCile like me to fix such a major problem and prove linux is... simply the best ! ! ! :-)

---

### Post by sponsoredwalk on 2007-11-20
OH MY GOD, I'm on my new 7.10 desktop posting this, during the install i partitioned as ext2 500mb and used 40gb as ext3. its fine. Thanx so much for the help i am going to reinstall and give myself more space.

---

### Post by ugm6hr on 2007-11-21
Glad things are looking good.  I suspect the problem may have been that there is a maximum ext2 partition size (is it around 2GB?)

---

