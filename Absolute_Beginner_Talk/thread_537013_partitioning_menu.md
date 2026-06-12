---
title: "partitioning menu"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by ragaz on 2007-08-28
hi everyone,

after hours of being convinced by my friends that Linux (and Ubuntu in particular) is the way to go i finally used the installation cd (feisty fawn) my good friend gave me, booted from it, and began to install. everything has gone fine so far, until step 4 of 7 (the partitioning section). I have two hard drives, one 320gb with vista (i didn't want it but it came standard with the new computer :P ), and the hard drive i would like to designate to  the Ubuntu OS to (120gb). in the beginning of step 4 i only had the option of "manually" partitioning the disk (when apparently according to all the documentation i have read so far there should also be an "automatic" option also). regardless i pressed forward with the manual option only to find the screen shot i have attached to this message.

i cannot see either of my drives to even begin selecting partitioning options. is this a problem that is out of my control? or am i so incredibly newb that Ubuntu is too much for me? :P

i did try and look up if this question has already been asked (because I'm sure that which ever Linux-pro reads this must get annoyed answering the same newb questions all the time) but i couldn't find anything. anyway, whatever help that could be offered would be VERY much appreciated :D 

thanks guys,
Ragaz

---

### Post by tszanon on 2007-08-28
Could you please go back to step 3 and take another screenshot? I've never seen something like this before. I think that in the step 3 you should have been able to select the disk, but I'm not sure.

---

### Post by ragaz on 2007-08-28
thank you VERY much for your quick reply! I'm impressed.

no, i don't get the option of selecting a drive before this point in installation:

step 1) select language (English)
step 2) selected location/timezone (Perth, Australia)
step 3) select keyboard type (US English)
step 4a) select if you want to partition manually (and in my case all i could choose was manually)
step 4b) the screen shot you saw

however, i have attached a screen shot for you of step 3 just in case there is something I'm missing :P

again thank you for your help

Ragaz

---

### Post by ragaz on 2007-08-28
hello again,

after tinkering a little more i found that when i plug in my 1gb thumb drive, the installer detects it. the only problem now is that i don't want it on the thumb drive! :D i have been playing around and found something in the system menu which shows devices. the problem seems to be that ubuntu just doesn't detect either of my hard drives. is there some way i can force ubuntu to search and detect the hard drives?

cheers again,
Ragaz

---

### Post by Hobo Joe on 2007-08-28
There is a program called GParted that is installed on the LiveCD, it's located under System > Adminstration. I find it's much better than the partitioner located on the installer.

---

### Post by ragaz on 2007-08-28
WOW hobo joe, respect to your ubuntu/coffee bean status. i didn't think i would be getting a 100% ubuntu guy in on this thread! cheers for the advice,

two probs though :P :
1) there isn't gparted on this live cd. instead there is GNOME Partition Editior (the closest thing i could find :S)
2) when i open that it only detects my thumb drive, i need it to detect my other two hard drives. 

what can i do? any more advice?

thanks again everyone,
Ryan

---

### Post by Tyke91 on 2007-08-28
GNOME Partition editor (GpartEd)

open that up and see if that helps :)

also - did you install the second hard drive yourself? if so, have you checked to make sure you did it correctly?

edit- just read your post, ouch... 

please type this into a console (applications, terminal)

```
sudo lshw
```

sudo gives you root access, and lshw is the command to show all of your system specs

please paste that in this forum with the tag "[code] [/_code]" (take away the underscore between / and code)

---

### Post by ragaz on 2007-08-29
hey, i am definitely gettin gthe pros in now :P

i tried gnome partition editor and, ye it only detects my thumb drive.

i opened the terminal as you said and typed in sudo... and get this

```

 x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KB
             capacity: 64KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 4MB
             capacity: 4MB
             capabilities: internal write-back instruction
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MB
             capacity: 8MB
             capabilities: internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 3035MB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 512MB
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: latency=0
                resources: iomemory:fd000000-fdffffff iomemory:c0000000-dfffffff iomemory:fa000000-fbffffff ioport:cc00-cc7f irq:10
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:bc00-bc1f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:b880-b89f irq:20
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:f9fffc00-f9ffffff irq:18
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   product: JUMPDRIVE SECURE
                   vendor: LEXAR MEDIA
                   physical id: 1
                   bus info: usb@2:1
                   logical name: scsi6
                   version: 30.00
                   serial: 106A1D03102846150606
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=480.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: JUMPDRIVE SECURE
                      vendor: LEXAR
                      physical id: 0.0.0
                      bus info: scsi@6:0.0.0
                      logical name: /dev/sde
                      version: 3000
                      serial: E3000070325052554BB4404
                      size: 991MB
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sde
                         size: 991MB
                         capabilities: partitioned partitioned:dos
                       *-volume
                            description: FAT16 <32M partition
                            physical id: 1
                            logical name: /dev/sde1
                            capacity: 991MB
                            capabilities: primary
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:f9ff8000-f9ffbfff irq:22
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-ide UNCLAIMED
                description: IDE interface
                product: Marvell Technology Group Ltd.
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@03:00.0
                version: b1
                width: 32 bits
                clock: 33MHz
                capabilities: ide bus_master cap_list
                configuration: latency=0
                resources: ioport:dc00-dc07 ioport:d880-d883 ioport:d800-d807 ioport:d480-d483 ioport:d400-d40f iomemory:feaffc00-feafffff irq:11
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:b800-b81f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:b480-b49f irq:21
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:b400-b41f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:f9fff800-f9fffbff irq:19
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb:0
                   description: Mass storage device
                   product: Super Multi DVD Rewriter
                   vendor: HL-DT-ST DVDRAM GSA-5163D
                   physical id: 3
                   bus info: usb@3:3
                   logical name: scsi4
                   version: 0.01
                   serial: 52227116
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=480.0MB/s
                 *-cdrom
                      description: DVD-RAM writer
                      product: DVDRAM GSA-5163D
                      vendor: HL-DT-ST
                      physical id: 0.0.0
                      bus info: scsi@4:0.0.0
                      logical name: /dev/cdrom
                      logical name: /dev/dvd
                      logical name: /dev/scd0
                      logical name: /dev/sr0
                      version: A104
                      capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                    *-disc
                         physical id: 0
                         logical name: /dev/cdrom
              *-usb:1
                   description: Mass storage device
                   product: Mass Storage Device
                   vendor: Generic
                   physical id: 6
                   bus info: usb@3:6
                   logical name: scsi5
                   version: 1.29
                   serial: 058F312D81B
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=250mA speed=480.0MB/s
                 *-disk:0
                      description: SCSI Disk
                      product: USB SD Reader
                      vendor: Generic
                      physical id: 0.0.0
                      bus info: scsi@5:0.0.0
                      logical name: /dev/sda
                      version: 1.00
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sda
                 *-disk:1
                      description: SCSI Disk
                      product: USB CF Reader
                      vendor: Generic
                      physical id: 0.0.1
                      bus info: scsi@5:0.0.1
                      logical name: /dev/sdb
                      version: 1.01
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdb
                 *-disk:2
                      description: SCSI Disk
                      product: USB SM Reader
                      vendor: Generic
                      physical id: 0.0.2
                      bus info: scsi@5:0.0.2
                      logical name: /dev/sdc
                      version: 1.02
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdc
                 *-disk:3
                      description: SCSI Disk
                      product: USB MS Reader
                      vendor: Generic
                      physical id: 0.0.3
                      bus info: scsi@5:0.0.3
                      logical name: /dev/sdd
                      version: 1.03
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdd
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-communication
                description: Modem
                product: Motorola
                vendor: Motorola
                physical id: 0
                bus info: pci@04:00.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: generic bus_master cap_list
                configuration: driver=serial latency=64 maxlatency=62 mingnt=1
                resources: iomemory:febff000-febfffff ioport:e800-e8ff irq:16
           *-network
                description: Ethernet interface
                product: RTL-8169SC Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@04:02.0
                logical name: eth0
                version: 10
                serial: 00:19:db:6b:4d:b1
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.8 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=twisted pair speed=100MB/s
                resources: ioport:e400-e4ff iomemory:febfec00-febfecff irq:20
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
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
             resources: ioport:b080-b087 ioport:b000-b003 ioport:ac00-ac07 ioport:a880-a883 ioport:a800-a80f ioport:a480-a48f irq:21
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: iomemory:f9fff400-f9fff4ff ioport:400-41f irq:5
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             logical name: scsi2
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:a080-a087 ioport:a000-a003 ioport:9c00-9c07 ioport:9880-9883 ioport:9800-980f ioport:9480-948f irq:21

```

i dont' know if that helps?

i'm sorry to be so much of a trouble guys, i wish i knew how to figure this out myself :S

Ryan

p.s. thanks for explaining the code you told me to type into the command line

---

### Post by reset3x on 2007-08-29
> **ragaz said:**
> hello again,

after tinkering a little more i found that when i plug in my 1gb thumb drive, the installer detects it. the only problem now is that i don't want it on the thumb drive! :D i have been playing around and found something in the system menu which shows devices. the problem seems to be that ubuntu just doesn't detect either of my hard drives. is there some way i can force ubuntu to search and detect the hard drives?

cheers again,
Ragaz

This is showing a USB Thumb Drive... Unmount and unplug it....

Then try the install again....

---

### Post by ragaz on 2007-08-29
thanks restet3x,

thats not the prob tho, because thats what i had originally (refer to my original posts). this seems like it is a big prob. lol noone (including the pros) has been able to solve it so far :P. when i unmount the thumb drive i'm back to square one where it doesnt' detect anything. i'm sure that the two hard drives are connected properly cz my vista OS detects them. i only just recently used vista to empty and move all the data that was on my storage (soon to be ubuntu) hard drive on to my windows harddrive.

what am i doing wrong? ](*,) lol :P

Ragaz

---

### Post by Tyke91 on 2007-08-29
hmm... im hoping more experienced users will back me up, but it doesnt look like there's a hard drive device anywhere in there...

you've got a usb flash drive

```
   description: SCSI Disk
                      product: JUMPDRIVE SECURE
                      vendor: LEXAR
                      physical id: 0.0.0
                      bus info: scsi@6:0.0.0
                      logical name: /dev/sde
                      version: 3000
                      serial: E3000070325052554BB4404
                      size: 991MB
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sde
                         size: 991MB
                         capabilities: partitioned partitioned:dos
                       *-volume
                            description: FAT16 <32M partition
                            physical id: 1
                            logical name: /dev/sde1
                            capacity: 991MB
                            capabilities: primar
```



but as far as i can see... no hard drives...


which brings me back to the question... did you install the 2nd hard drive yourself?

edit:

im just comparing it to mine, which has a hard drive with two partitions... it should look something like this

```
 *-disk
                description: SCSI Disk
                product: SAMSUNG HD160JJ/
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: ZM10
                serial: S0DFJ1QLC01320
                size: 149GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 30GB
                   capabilities: primary
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 114GB
                   capabilities: primary bootable
              *-volume:2
                   description: Linux swap / Solaris partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 4714MB
                   capabilities: primary nofs

```

---

### Post by ragaz on 2007-08-29
thanks tyke for replying so soon. its people like you that keep the ubuntu world turning.

but your right i went through it myself and could see anything that represented eithe rof my two seperate hdds (i have a 320gb one and a 120gb one). the 320gb one was installed by the company i brought it from and the 120gb one was from my previous computer which i installed myself (as i have in the past. with my old system i put alot of it together). i'm pretty sure i have installed the harddrives correctly. i have used the cable select option for the pin configuation on the back of them, but none the less my 320gb drive is still the master and 120gb is the slave. the thing is i have now restarted my computer and loaded back up vista and vista detects BOTH the drives (including the empty 120gb that i formatted with vista when i first instaled the drive). is it the fact that they are both partitioned already as ntfs from windows that linux doesnt' want to see them?

again thanks tyke for all of your help.
Ryan

---

### Post by dwhitney67 on 2007-08-29
Looks like you have a SCSI HDD.  Is this correct?  If this is the case, is there perhaps an option you need to pass to the kernel when you boot from the LiveCD?

---

### Post by s[_]spect on 2007-08-29
Assuming you formatted the new drive NTFS and linux wont be able to write to this with additional util.. best bet is to go back to vista.. open disk manager and remove the partition on this disk.. leave it blank.. the try the ubuntu install again. Cheers

---

### Post by xaco1234 on 2007-08-29
> **'s[_]spect said:**
> Assuming you formatted the new drive NTFS and linux wont be able to write to this with additional util.. best bet is to go back to vista.. open disk manager and remove the partition on this disk.. leave it blank.. the try the ubuntu install again. Cheers

that shoudn't be a problem, i installed ubuntu last night over an ntfs drive, had to reformat it to ext3 and a swap, but there wasn't a problem wit it

---

### Post by ragaz on 2007-08-29
hey guys, thanks for having a crack at this problem :P

my two hdds are (acording to vista's system description thing):
1) ST3320620AS ATA Device (320GB, the one with vista on it)
2) Maxtor 6l120PO ATA Device (120GB, the one that has been partitioned as NTFS but is empty and i want it to be the ubuntu drive)

now, i'm studying electrical power engineering, ie i'm still fairly newbish when it comes to electronics however i thought that ATA stood for advanced technology attached or something along those lines, but it basically ment IDE. which is different to SCUSI isn't it?

what is the group concencus on deleting the partition on the Maxtor and then reloading linux and seeing if it detects it then? worth a shot or not?

thanks guys for helping out, i really appresiate it and if you even need power factor corrections done for you houses or something send me an email :P (i don't think i'll be able to put much into the ubuntu project untill i get linux working on my computer and learning and tinkering with it so i can help out newbs one day just like you ultra coffee bean guys are doing atm) :D

Ragaz

---

### Post by tszanon on 2007-08-29
> **ragaz said:**
> what is the group concencus on deleting the partition on the Maxtor and then reloading linux and seeing if it detects it then? worth a shot or not?

It shouldn't be necessary to delete the partition before installing but, since nothing has solved the problem yet, I would try deleting the partition and then installing.

Edit: another suggestion: have you tried to use the Alternate CD? Text-mode installation isn't harder than graphical installation, and maybe it works.

---

### Post by reset3x on 2007-09-01
> **ragaz said:**
> thanks tyke for replying so soon. its people like you that keep the ubuntu world turning.

but your right i went through it myself and could see anything that represented eithe rof my two seperate hdds (i have a 320gb one and a 120gb one). the 320gb one was installed by the company i brought it from and the 120gb one was from my previous computer which i installed myself (as i have in the past. with my old system i put alot of it together). i'm pretty sure i have installed the harddrives correctly. i have used the cable select option for the pin configuation on the back of them, but none the less my 320gb drive is still the master and 120gb is the slave. the thing is i have now restarted my computer and loaded back up vista and vista detects BOTH the drives (including the empty 120gb that i formatted with vista when i first instaled the drive). is it the fact that they are both partitioned already as ntfs from windows that linux doesnt' want to see them?

again thanks tyke for all of your help.
Ryan

Try Jumpering them as a master and slave if they're on the same cable..... Or configure one drive (the 120) as a master on the cable with your CD drive and make your CD a slave.... That would make transfers faster between the two drives.....

Hope this is a cure for you........

---

