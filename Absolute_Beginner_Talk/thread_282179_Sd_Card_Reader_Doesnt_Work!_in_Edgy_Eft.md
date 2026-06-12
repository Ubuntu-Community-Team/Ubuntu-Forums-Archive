---
title: "Sd Card Reader Doesnt Work! in Edgy Eft"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by xmux on 2006-10-22
Hi!

I have a problem with my SD card reader.. In Dapper times people were saying that the SD card reader will work perfectly in Edgy Eft and now i have Edgy Eft and my SD card reader doesnt work!! What can i do? i have a Toshiba Laptop and i tried almost all the forums and google pages that i found but its doesnt work... :( do u have some suggestions? (please dont tell me buy a external sd card reader 'cause this is not the solution, its running away from problem..)

Thanks.

---

### Post by dbott67 on 2006-10-22
I've got a Ricoh card reader built into my Dell 6400.  The (edited) output of **sudo lshw** gives me the following:
```
 *-firewire
                description: FireWire (IEEE 1394)
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@03:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:df9fd800-df9fdfff irq:177
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@03:01.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci
                resources: iomemory:df9fd400-df9fd4ff irq:66
           *-system:1 UNCLAIMED
                description: System peripheral
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@03:01.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:df9fd500-df9fd5ff irq:9
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@03:01.3
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:df9fd600-df9fd6ff irq:9
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.4
                bus info: pci@03:01.4
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:df9fd700-df9fd7ff irq:9

```

Some folks have suggested booting the system with the card in place.

```
dbott@dapper:~$ mount
/dev/sda7 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-686/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda2 on /media/sda2 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda5 on /media/sda5 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda6 on /media/sda6 type ntfs (rw,nls=utf8,umask=007,gid=46)
//192.168.1.2/Music on /home/dbott/music type smbfs (rw)
**/dev/mmcblk0p1 on /media/mmcdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)**

```

---

### Post by xmux on 2006-10-22
Hi;

i got this one with the first:
```

    description: Notebook
    product: Satellite M30
    vendor: TOSHIBA
    version: PSM30E-71022-TR
    serial: 74624011G
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=enabled uuid=7EFE4C80-B0FD-17A2-8030-B1D774624011
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: $$C04773WV
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.50 (05/19/2004)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pcmcia upgrade shadowing vesa escd cdboot bootselect pcmciaboot edd int13floppy720 int5printscreen int9keyboard int17printer acpi usb agp biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.6
          slot: uFC-PGA Socket
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 64KB
             capacity: 64KB
             clock: 1GHz (1ns)
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 2MB
             capacity: 2MB
             clock: 1GHz (1ns)
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 512MB
          capacity: 2GB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 0
             size: 512MB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous [empty]
             physical id: 1
             slot: DIMM 1
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: d0000000
          bus info: pci@00:00.0
          version: 21
          width: 32 bits
          clock: 33MHz
          resources: iomemory:d0000000-dfffffff
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 21
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV34M [GeForce FX Go5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:c1000000-c1ffffff iomemory:e0000000-efffffff irq:10
        *-usb:0
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
             resources: ioport:1800-181f irq:3
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Microsoft Notebook/Mobile Optical Mouse 2.0
                   vendor: Microsoft
                   physical id: 2
                   bus info: usb@1:2
                   version: 2.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
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
             resources: ioport:1820-183f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
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
             resources: iomemory:c0000000-c00003ff irq:7
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   product: USB2.0 Storage Device
                   vendor: Cypress Semiconductor
                   physical id: 3
                   bus info: usb@3:3
                   logical name: scsi1
                   version: 0.01
                   serial: DEF10BA906D6
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=0mA speed=480.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: SP2014N
                      vendor: SAMSUNG
                      physical id: 0.0.0
                      bus info: scsi@1:0.0.0
                      logical name: /dev/sda
                      version: 0000
                      serial: 0S881JLJ
                      size: 186GB
                      capabilities: partitioned partitioned:dos
                    *-volume:0
                         description: HPFS/NTFS partition
                         physical id: 1
                         bus info: scsi@1:0.0.0,1
                         logical name: /dev/sda1
                         capacity: 58GB
                         capabilities: primary
                    *-volume:1
                         description: HPFS/NTFS partition
                         physical id: 2
                         bus info: scsi@1:0.0.0,2
                         logical name: /dev/sda2
                         capacity: 58GB
                         capabilities: primary
                    *-volume:2
                         description: HPFS/NTFS partition
                         physical id: 3
                         bus info: scsi@1:0.0.0,3
                         logical name: /dev/sda3
                         capacity: 69GB
                         capabilities: primary
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 7
                bus info: pci@02:07.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:c2006000-c20067ff iomemory:c2000000-c2003fff irq:3
           *-network:0
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@02:08.0
                logical name: eth0
                version: 83
                serial: 00:0e:7b:2d:23:17
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
                resources: iomemory:c2004000-c2004fff ioport:3000-303f irq:11
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: a
                bus info: pci@02:0a.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:36:b6:06
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.1.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.231 link=yes multicast=yes wireless=IEEE 802.11b
                resources: iomemory:c2005000-c2005fff irq:11
           *-pcmcia
                description: CardBus bridge
                product: ToPIC100 PCI to Cardbus Bridge with ZV Support
                vendor: Toshiba America Info Systems
                physical id: b
                bus info: pci@02:0b.0
                version: 33
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:c2007000-c2007fff irq:3
           *-system UNCLAIMED
                description: System peripheral
                product: SD TypA Controller
                vendor: Toshiba America Info Systems
                physical id: d
                bus info: pci@02:0d.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:c2006800-c20069ff irq:3
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
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
             resources: ioport:1840-184f iomemory:32000000-320003ff irq:11
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: TOSHIBA MK4021GAS
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: GA224G
                   serial: 83AG6548T
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 12GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux swap / Solaris partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 1027MB
                      capabilities: primary nofs
                 *-volume:2
                      description: Linux filesystem partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 298MB
                      capabilities: primary
                 *-volume:3
                      description: Extended partition
                      physical id: 4
                      bus info: ide@0.0,4
                      logical name: /dev/hda4
                      capacity: 23GB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: MATSHITADVD-RAM UJ-820S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.00
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-multimedia
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
             resources: ioport:1c00-1cff ioport:1880-18bf iomemory:c0000c00-c0000dff iomemory:c0000800-c00008ff irq:4
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             resources: ioport:2400-24ff ioport:2000-207f irq:4
  *-battery
       description: Lithium Ion Battery
       product: LP644E
       vendor: TOSHIBA
       physical id: 1
       version: 04/06/14
       serial: 1100037902
       slot: 1st Battery
       configuration: voltage=10.8V
```


!!!!the second one is:

```
/dev/hda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/hda3 on /boot type ext3 (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
```

---

### Post by dbott67 on 2006-10-22
Is it built-in or is it a USB plug-in model? EDIT: oops, I see that you posted it was internal... nevermind.

What happens if you re-boot the system with the card in?

-Dave

---

### Post by dbott67 on 2006-10-22
Some other info I've come across seems to suggest that the problem lies in some of the newer kernels... using older kernels may help.

This thread offers some additional suggestions:
[http://www.ubuntuforums.org/showthread.php?t=224131&highlight=mount+sd+card](http://www.ubuntuforums.org/showthread.php?t=224131&highlight=mount+sd+card)

---

### Post by xmux on 2006-10-22
no way when i reboot the system with the card it doesnt appears anything...

---

### Post by dbott67 on 2006-10-22
I'm afraid I'm out of ideas.  :(

By looking at your lshw output, I don't even see the SD Card Reader hardware.  There are a number of threads on the issue, but they appear to be able to detect the hardware, just not mount the card.

You'll have to keep perusing the forums (or Google at large) to see if you can find a solution.

Good luck (and if you find anything, please post a HOWTO back here).

-Dave

---

### Post by xmux on 2006-10-22
i found something when i write lspci than i get

```

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0a.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)

```

and at the last Toshiba America Info Systems SD.... i think its something with this one but i am not so sure... HELP!!

---

### Post by xmux on 2006-10-23
Noone has the same Problem???? i think i must change the laptop!!

---

### Post by dbott67 on 2006-10-23
With the SD card installed, do you see an entry in **/dev** the starts with mmc?  Similar to **/dev/mmcblk0** (the device) and **/dev/mmcblk0p1** (the partition).

I'm also wondering if the module is loaded in Edgy.  Here's the output on my lsmod:
```
dbott@dapper:~$ lsmod
Module                  Size  Used by
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54212  4 rfcomm,l2cap
ppdev                   9668  0
fglrx                 391756  61
speedstep_centrino      8752  1
cpufreq_userspace       6496  2
cpufreq_stats           6688  0
freq_table              4928  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               22848  1 i2c_acpi_ec
ipv6                  286976  26
smbfs                  71576  2
ndiswrapper           200308  0
nls_utf8                2240  4
ntfs                  111728  3
nls_iso8859_1           4224  1
nls_cp437               5888  2
vfat                   14496  2
fat                    55548  1 vfat
dm_mod                 63256  1
af_packet              24520  4
md_mod                 76052  0
sbp2                   25060  0
parport_pc             37988  0
lp                     12356  0
parport                39400  3 ppdev,parport_pc,lp
joydev                 10432  0
tsdev                   8032  0
sdhci                  16096  0
mmc_core               31816  3 sdhci
pcspkr                  2244  0
b44                    27980  0
mii                     6176  1 b44
snd_hda_intel          20468  1
snd_hda_codec         166096  1 snd_hda_intel
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
psmouse                40004  0
serio_raw               7748  0
snd_timer              26884  1 snd_pcm
snd                    60004  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm
usbhid                 42752  0
intel_agp              24700  1
hw_random               5716  0
agpgart                36784  2 fglrx,intel_agp
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
evdev                  10176  2
sr_mod                 17988  0
sg                     40160  0
cdrom                  41408  1 sr_mod
ext3                  148296  1
jbd                    65876  1 ext3
ide_generic             1504  0
ohci1394               37524  0
ieee1394              306520  2 sbp2,ohci1394
ehci_hcd               36104  0
uhci_hcd               35536  0
usbcore               139172  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
[COLOR="Red"]sd_mod                 20448  7[/COLOR]
generic                 5124  0
ata_piix               11364  12
libata                 83440  1 ata_piix
[COLOR="Red"]scsi_mod              145960  5 sbp2,sr_mod,sg,sd_mod,libata[/COLOR]
thermal                13768  0
processor              26888  2 speedstep_centrino,thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  74
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit
dbott@dapper:~$
```

The 2 modules that are required are: **sd_mod** & **scsi_mod** (I think).  I found a page [here]("http://www.cs.sfu.ca/~ggbaker/personal/cf-linux") that explains how to get a card reader going in Linux.

-Dave

---

### Post by xmux on 2006-10-24
when i write lsmod i got this

```
Module                  Size  Used by
ch                     17032  0
st                     41500  0
osst                   56864  0
sr_mod                 18212  0
battery                11652  0
ac                      6788  0
thermal                15624  0
fan                     6020  0
button                  7952  0
ipw2200               115652  0
ieee80211              35272  1 ipw2200
ieee80211_crypt         7552  1 ieee80211
e100                   38020  0
mii                     6912  1 e100
nls_cp437               6912  0
isofs                  38076  0
udf                    89348  0
sg                     37404  0
sd_mod                 22656  0
usb_storage            75072  0
libusual               17040  1 usb_storage
rfcomm                 42260  0
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
speedstep_centrino      9760  1
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  1
cpufreq_conservative     8712  0
video                  17540  0
toshiba_acpi           12224  0
tc1100_wmi              8324  0
sony_acpi               6412  0
sbs                    16804  0
pcc_acpi               14080  0
i2c_ec                  6272  1 sbs
hotkey                 11556  0
dev_acpi               12292  0
container               5632  0
asus_acpi              17688  0
ipv6                  272288  10
nls_utf8                3200  1
af_packet              24584  4
ntfs                  112116  1
sbp2                   24584  0
scsi_mod              144648  8 ch,st,osst,sr_mod,sg,sd_mod,usb_storage,sbp2
lp                     12964  0
pcmcia                 40380  0
yenta_socket           28812  1
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           34844  5
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
usbhid                 45152  0
nvidia               4555092  12
snd_pcm                84612  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  3 snd_pcm
joydev                 11200  0
tsdev                   9152  0
intel_agp              26012  1
agpgart                34888  2 nvidia,intel_agp
i2c_core               23424  2 i2c_ec,nvidia
snd                    58372  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
parport_pc             37796  1
parport                39496  2 lp,parport_pc
serio_raw               8452  0
pcspkr                  4352  0
evdev                  11392  2
psmouse                41352  0
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
ext3                  142728  2
jbd                    62228  1 ext3
ohci1394               37040  0
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0
uhci_hcd               24968  0
usbcore               134912  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0
ide_cd                 33696  0
cdrom                  38944  2 sr_mod,ide_cd
ide_disk               18560  5
piix                   11780  1
generic                 5764  0
processor              31560  2 thermal,speedstep_centrino
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability

```


than in my /dev section there is only these...
```
acpi       ptya9  ptydd  ptyr1  ptyu5  ptyx9  ram7      tty42  ttyb9  ttyed  ttyS0  ttyv1  ttyy5
adsp       ptyaa  ptyde  ptyr2  ptyu6  ptyxa  ram8      tty43  ttyba  ttyee  ttys1  ttyv2  ttyy6
agpgart    ptyab  ptydf  ptyr3  ptyu7  ptyxb  ram9      tty44  ttybb  ttyef  ttyS1  ttyv3  ttyy7
audio      ptyac  ptye0  ptyr4  ptyu8  ptyxc  random    tty45  ttybc  ttyp0  ttys2  ttyv4  ttyy8
bus        ptyad  ptye1  ptyr5  ptyu9  ptyxd  rtc       tty46  ttybd  ttyp1  ttyS2  ttyv5  ttyy9
cdrom      ptyae  ptye2  ptyr6  ptyua  ptyxe  scsi      tty47  ttybe  ttyp2  ttys3  ttyv6  ttyya
cdrw       ptyaf  ptye3  ptyr7  ptyub  ptyxf  shm       tty48  ttybf  ttyp3  ttyS3  ttyv7  ttyyb
console    ptyb0  ptye4  ptyr8  ptyuc  ptyy0  snapshot  tty49  ttyc0  ttyp4  ttys4  ttyv8  ttyyc
core       ptyb1  ptye5  ptyr9  ptyud  ptyy1  snd       tty5   ttyc1  ttyp5  ttys5  ttyv9  ttyyd
disk       ptyb2  ptye6  ptyra  ptyue  ptyy2  sndstat   tty50  ttyc2  ttyp6  ttys6  ttyva  ttyye
dsp        ptyb3  ptye7  ptyrb  ptyuf  ptyy3  stderr    tty51  ttyc3  ttyp7  ttys7  ttyvb  ttyyf
dvd        ptyb4  ptye8  ptyrc  ptyv0  ptyy4  stdin     tty52  ttyc4  ttyp8  ttys8  ttyvc  ttyz0
dvdrw      ptyb5  ptye9  ptyrd  ptyv1  ptyy5  stdout    tty53  ttyc5  ttyp9  ttys9  ttyvd  ttyz1
fb0        ptyb6  ptyea  ptyre  ptyv2  ptyy6  toshiba   tty54  ttyc6  ttypa  ttysa  ttyve  ttyz2
fd         ptyb7  ptyeb  ptyrf  ptyv3  ptyy7  tty       tty55  ttyc7  ttypb  ttysb  ttyvf  ttyz3
full       ptyb8  ptyec  ptys0  ptyv4  ptyy8  tty0      tty56  ttyc8  ttypc  ttysc  ttyw0  ttyz4
hda        ptyb9  ptyed  ptys1  ptyv5  ptyy9  tty1      tty57  ttyc9  ttypd  ttysd  ttyw1  ttyz5
hda1       ptyba  ptyee  ptys2  ptyv6  ptyya  tty10     tty58  ttyca  ttype  ttyse  ttyw2  ttyz6
hda2       ptybb  ptyef  ptys3  ptyv7  ptyyb  tty11     tty59  ttycb  ttypf  ttysf  ttyw3  ttyz7
hda3       ptybc  ptyp0  ptys4  ptyv8  ptyyc  tty12     tty6   ttycc  ttyq0  ttyt0  ttyw4  ttyz8
hda4       ptybd  ptyp1  ptys5  ptyv9  ptyyd  tty13     tty60  ttycd  ttyq1  ttyt1  ttyw5  ttyz9
hda5       ptybe  ptyp2  ptys6  ptyva  ptyye  tty14     tty61  ttyce  ttyq2  ttyt2  ttyw6  ttyza
hdc        ptybf  ptyp3  ptys7  ptyvb  ptyyf  tty15     tty62  ttycf  ttyq3  ttyt3  ttyw7  ttyzb
hpet       ptyc0  ptyp4  ptys8  ptyvc  ptyz0  tty16     tty63  ttyd0  ttyq4  ttyt4  ttyw8  ttyzc
initctl    ptyc1  ptyp5  ptys9  ptyvd  ptyz1  tty17     tty7   ttyd1  ttyq5  ttyt5  ttyw9  ttyzd
input      ptyc2  ptyp6  ptysa  ptyve  ptyz2  tty18     tty8   ttyd2  ttyq6  ttyt6  ttywa  ttyze
kmem       ptyc3  ptyp7  ptysb  ptyvf  ptyz3  tty19     tty9   ttyd3  ttyq7  ttyt7  ttywb  ttyzf
kmsg       ptyc4  ptyp8  ptysc  ptyw0  ptyz4  tty2      ttya0  ttyd4  ttyq8  ttyt8  ttywc  urandom
log        ptyc5  ptyp9  ptysd  ptyw1  ptyz5  tty20     ttya1  ttyd5  ttyq9  ttyt9  ttywd  vcs
loop0      ptyc6  ptypa  ptyse  ptyw2  ptyz6  tty21     ttya2  ttyd6  ttyqa  ttyta  ttywe  vcs1
lp0        ptyc7  ptypb  ptysf  ptyw3  ptyz7  tty22     ttya3  ttyd7  ttyqb  ttytb  ttywf  vcs2
MAKEDEV    ptyc8  ptypc  ptyt0  ptyw4  ptyz8  tty23     ttya4  ttyd8  ttyqc  ttytc  ttyx0  vcs3
mem        ptyc9  ptypd  ptyt1  ptyw5  ptyz9  tty24     ttya5  ttyd9  ttyqd  ttytd  ttyx1  vcs4
mixer      ptyca  ptype  ptyt2  ptyw6  ptyza  tty25     ttya6  ttyda  ttyqe  ttyte  ttyx2  vcs5
net        ptycb  ptypf  ptyt3  ptyw7  ptyzb  tty26     ttya7  ttydb  ttyqf  ttytf  ttyx3  vcs6
null       ptycc  ptyq0  ptyt4  ptyw8  ptyzc  tty27     ttya8  ttydc  ttyr0  ttyu0  ttyx4  vcs7
nvidia0    ptycd  ptyq1  ptyt5  ptyw9  ptyzd  tty28     ttya9  ttydd  ttyr1  ttyu1  ttyx5  vcs8
nvidiactl  ptyce  ptyq2  ptyt6  ptywa  ptyze  tty29     ttyaa  ttyde  ttyr2  ttyu2  ttyx6  vcsa
port       ptycf  ptyq3  ptyt7  ptywb  ptyzf  tty3      ttyab  ttydf  ttyr3  ttyu3  ttyx7  vcsa1
ppp        ptyd0  ptyq4  ptyt8  ptywc  ram0   tty30     ttyac  ttye0  ttyr4  ttyu4  ttyx8  vcsa2
psaux      ptyd1  ptyq5  ptyt9  ptywd  ram1   tty31     ttyad  ttye1  ttyr5  ttyu5  ttyx9  vcsa3
ptmx       ptyd2  ptyq6  ptyta  ptywe  ram10  tty32     ttyae  ttye2  ttyr6  ttyu6  ttyxa  vcsa4
pts        ptyd3  ptyq7  ptytb  ptywf  ram11  tty33     ttyaf  ttye3  ttyr7  ttyu7  ttyxb  vcsa5
ptya0      ptyd4  ptyq8  ptytc  ptyx0  ram12  tty34     ttyb0  ttye4  ttyr8  ttyu8  ttyxc  vcsa6
ptya1      ptyd5  ptyq9  ptytd  ptyx1  ram13  tty35     ttyb1  ttye5  ttyr9  ttyu9  ttyxd  vcsa7
ptya2      ptyd6  ptyqa  ptyte  ptyx2  ram14  tty36     ttyb2  ttye6  ttyra  ttyua  ttyxe  vcsa8
ptya3      ptyd7  ptyqb  ptytf  ptyx3  ram15  tty37     ttyb3  ttye7  ttyrb  ttyub  ttyxf  xconsole
ptya4      ptyd8  ptyqc  ptyu0  ptyx4  ram2   tty38     ttyb4  ttye8  ttyrc  ttyuc  ttyy0  zero
ptya5      ptyd9  ptyqd  ptyu1  ptyx5  ram3   tty39     ttyb5  ttye9  ttyrd  ttyud  ttyy1
ptya6      ptyda  ptyqe  ptyu2  ptyx6  ram4   tty4      ttyb6  ttyea  ttyre  ttyue  ttyy2
ptya7      ptydb  ptyqf  ptyu3  ptyx7  ram5   tty40     ttyb7  ttyeb  ttyrf  ttyuf  ttyy3
ptya8      ptydc  ptyr0  ptyu4  ptyx8  ram6   tty41     ttyb8  ttyec  ttys0  ttyv0  ttyy4

```

---

### Post by dbott67 on 2006-10-24
This [thread]("http://ubuntuforums.org/showpost.php?p=1651036&postcount=46") suggests doing the following:

```
sudo apt-get install ivman
``` which is a daemon to auto-mount and manage media devices.

There seems to be an unconfirmed write-up in launchpad:
[https://launchpad.net/distros/ubuntu/+source/gnome-volume-manager/+bug/67307](https://launchpad.net/distros/ubuntu/+source/gnome-volume-manager/+bug/67307)

On my computer, a listing of loaded modules beginning with sd* and scsi* gives:
```
dbott@thedrake:~$ modprobe -l sd*
[COLOR="Red"]/lib/modules/2.6.15-27-386/kernel/drivers/scsi/sd_mod.ko[/COLOR] <-- this seems to be missing on your computer
/lib/modules/2.6.15-27-386/kernel/drivers/net/wan/sdla.ko
/lib/modules/2.6.15-27-386/kernel/drivers/mmc/sdhci.ko
```
```

dbott@thedrake:~$ modprobe -l scsi*
modprobe -l scsi*
/lib/modules/2.6.15-27-386/kernel/drivers/scsi/scsi_transport_spi2.ko
/lib/modules/2.6.15-27-386/kernel/drivers/scsi/scsi_transport_spi.ko
/lib/modules/2.6.15-27-386/kernel/drivers/scsi/scsi_transport_sas.ko
/lib/modules/2.6.15-27-386/kernel/drivers/scsi/scsi_transport_iscsi.ko
[COLOR="Red"]/lib/modules/2.6.15-27-386/kernel/drivers/scsi/scsi_mod.ko[/COLOR] <-- this seems to be missing on your computer
/lib/modules/2.6.15-27-386/kernel/drivers/scsi/scsi_debug.ko
/lib/modules/2.6.15-27-386/kernel/drivers/scsi/scsi_transport_fc.ko

```

You might want to try to load the modules manually:
```
sudo modprobe sd_mod
```
```
sudo modprobe scsi_mod
```

-Dave

---

### Post by xmux on 2006-10-25
Hey i got something when i write
modprobe -l sd*
i got this!
```
/lib/modules/2.6.17-10-generic/kernel/drivers/mmc/sdhci.ko
```

than i look also

modprobe -l scsi*
```
/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/scsi_transport_spi.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/scsi_transport_sas.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/scsi_transport_iscsi.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/scsi_transport_fc.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/scsi_mod.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/scsi_debug.ko
```
than i got this one, i think my kernel is generic thats why its doesnt work maybe up Tomorrow the kernel will be stabil and than it will work maybe?? Because your kernel is older than mine..

---

### Post by dbott67 on 2006-10-25
Yes, it may be that it's not compiled in the kernel yet.  A few things to consider:

1. Try the **sudo apt-get install ivman**

*I would try this first, as it's an easy add from the repos & you can always remove it if it doesn't work.*

2. Downgrade your kernel to an older version.

*Kind of a pain, but it would allow you to confirm or eliminate the kernel.*

Can you load the modules manually?
```
sudo modprobe sd_mod
```
```
sudo modprobe scsi_mod *<-- this one appears to be loaded already.*
``` 

I'm not sure what the sdhci module does.  The module required (I think) is **sd_mod**.

_**Update:**_

The sdhci module is for media/flash, so it appears to be required (at least according to the thread below, and it's loaded on my PC as well).

Googling **sdhci.ko** gave me this link ([http://fedoraforum.org/forum/showthread.php?t=115206&page=1&pp=15](http://fedoraforum.org/forum/showthread.php?t=115206&page=1&pp=15)) that has some good suggestions to try.

-Dave

---

### Post by LinuxFab on 2006-10-27
Well, Im happy Im not alone :-? 
I have the same issue here, everything was fine till.... I upgraded the whole thing a few days ago (Edgy Eft on laptop HP NX6125)
The SD Card was read without any problem at all. I can't say the same now. I really want to take a look at the pictures I took some days ago (actually, I wanted to send a few of them by email)

How come ??
Same about ATI Radeon 3D Acceleration. Same about GAIM Beta2 (had to manually create a symbolic link) and a few other apps...
and my 'screen config keys' still do NOT work (FN key + F9/F10)

Any help appreciated thanks
(sorry about my english)

---

### Post by IngFreeman on 2006-10-28
First, excuse me for bad english, so:
i have an HP dv4266 notebook and edgy ubuntu installed on. I have the same problem, but i have found a solution (if it's corrected i don't know but it works for me):
the solution is for Texas Instrument integrated card reader and you can find it [here]("http://www.webcon.ca/~imorgan/tifm21/")

so i ask: what is the correct way to add this startup script to the edgy?
thank you!

---

### Post by rrwo on 2006-10-30
I'm having the same problem with my ThinkPad Z60m (now running Edgy, Linux 2.6.17-10-386).

The SD card reader does not work at all, even when booting the system with the card inside.  

When inserting the card, the light usually doesn't go on. (Sometimes it blinks briefly.)

There is no device resembling /dev/mmc*.

I haven't the slightest idea how to get this to work.

---

### Post by leomcabral on 2006-10-30
Try this,

$ sudo modprobe tifm_sd

Insert your sd card to test it. If it works correctaly edit /etc/modules (sudo gedit /etc/modules) and add in the last line (new line) tifm_sd

---

### Post by xmux on 2006-10-30
Hey i have some news!! i installed the Ubuntu 6.10 with gnome and it has some new things in it!! when i write 

sudo lshw	it gives me this!!

```
xmux-laptop               
    description: Notebook
    product: Satellite M30
    vendor: TOSHIBA
    version: PSM30E-71022-TR
    serial: 74624011G
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=enabled uuid=7EFE4C80-B0FD-17A2-8030-B1D774624011
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: $$C04773WV
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.50 (05/19/2004)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pcmcia upgrade shadowing vesa escd cdboot bootselect pcmciaboot edd int13floppy720 int5printscreen int9keyboard int17printer acpi usb agp biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.6
          slot: uFC-PGA Socket
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 64KB
             capacity: 64KB
             clock: 1GHz (1ns)
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 2MB
             capacity: 2MB
             clock: 1GHz (1ns)
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 512MB
          capacity: 2GB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 0
             size: 512MB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous [empty]
             physical id: 1
             slot: DIMM 1
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: d0000000
          bus info: pci@00:00.0
          version: 21
          width: 32 bits
          clock: 33MHz
          resources: iomemory:d0000000-dfffffff
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 21
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV34M [GeForce FX Go5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:c1000000-c1ffffff iomemory:e0000000-efffffff irq:10
        *-usb:0
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
             resources: ioport:1800-181f irq:3
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Microsoft Notebook/Mobile Optical Mouse 2.0
                   vendor: Microsoft
                   physical id: 2
                   bus info: usb@1:2
                   version: 2.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
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
             resources: ioport:1820-183f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
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
             resources: iomemory:c0000000-c00003ff irq:7
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 7
                bus info: pci@02:07.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:c2006000-c20067ff iomemory:c2000000-c2003fff irq:3
           *-network:0
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@02:08.0
                logical name: eth0
                version: 83
                serial: 00:0e:7b:2d:23:17
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
                resources: iomemory:c2004000-c2004fff ioport:3000-303f irq:11
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: a
                bus info: pci@02:0a.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:36:b6:06
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.1.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.228 link=yes multicast=yes wireless=IEEE 802.11b
                resources: iomemory:c2005000-c2005fff irq:11
           *-pcmcia
                description: CardBus bridge
                product: ToPIC100 PCI to Cardbus Bridge with ZV Support
                vendor: Toshiba America Info Systems
                physical id: b
                bus info: pci@02:0b.0
                version: 33
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:c2007000-c2007fff irq:3
           *-system UNCLAIMED
                description: System peripheral
                product: SD TypA Controller
                vendor: Toshiba America Info Systems
                physical id: d
                bus info: pci@02:0d.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:c2006800-c20069ff irq:3
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
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
             resources: ioport:1840-184f iomemory:32000000-320003ff irq:11
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: TOSHIBA MK4021GAS
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: GA224G
                   serial: 83AG6548T
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 12GB
                      capabilities: primary bootable
                 *-volume:1
                      description: W95 FAT32 partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 12GB
                      capabilities: primary
                 *-volume:2
                      description: Linux swap / Solaris partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 1090MB
                      capabilities: primary nofs
                 *-volume:3
                      description: Extended partition
                      physical id: 4
                      bus info: ide@0.0,4
                      logical name: /dev/hda4
                      capacity: 11GB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: MATSHITADVD-RAM UJ-820S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.00
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-multimedia
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
             resources: ioport:1c00-1cff ioport:1880-18bf iomemory:c0000c00-c0000dff iomemory:c0000800-c00008ff irq:4
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             resources: ioport:2400-24ff ioport:2000-207f irq:4
  *-battery
       description: Lithium Ion Battery
       product: LP644E
       vendor: TOSHIBA
       physical id: 1
       version: 04/06/14
       serial: 1100037902
       slot: 1st Battery
       configuration: voltage=10.8V 
```

than i wrote mount
```

/dev/hda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda2 on /media/hda2 type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

and i got this mod

modprobe -l sd*
```

/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/sd_mod.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/net/wan/sdla.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/mmc/sdhci.ko[

```

and modprobe -l scsi*

```

/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/scsi_transport_spi.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/scsi_transport_sas.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/scsi_transport_iscsi.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/scsi_transport_fc.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/scsi_mod.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/scsi_debug.ko

```

and now i have a similar system like dbott67 but i have still the same problem like before when i put the card inside it doesnt appears anything!!!

any help more????

---

### Post by xmux on 2006-10-30
> 

$ sudo modprobe tifm_sd

Insert your sd card to test it. If it works correctaly edit /etc/modules (sudo gedit /etc/modules) and add in the last line (new line) tifm_sd


and i tried also this one but nothing happens!!!

Did someone solved that Problem or nobody doesnt want to loose time with this???

---

### Post by rrwo on 2006-10-30
modprobe tifm_sd doesn't work for me. (As I don't have a TI controller, should I have expected it to work...?)

---

### Post by dgregory81 on 2006-10-31
```
sudo apt-get install ivman
```

This works, it's for gnome though, anyone know of a kde alternative for our Kubuntu friends?

install ivman then type:

```
sudo /etc/init.d/ivman start
```

Then reinsert your card it will read SD for sure, I don't know about xD or memory stick.

FYI my card reader is a Texas Instruments.  So i can't say for sure it will work on others.

Anyone know how to get this to run at startup?

---

### Post by alchimera on 2006-10-31
> **leomcabral said:**
> Try this,

$ sudo modprobe tifm_sd

Insert your sd card to test it. If it works correctaly edit /etc/modules (sudo gedit /etc/modules) and add in the last line (new line) tifm_sd

Worked for me, thanks!

---

### Post by rrwo on 2006-10-31
I don't have an mmc_block module (I do have mmc_core though). Could that be an issue?

---

### Post by xmux on 2006-11-01
ivman doesnt work for me!! i think i must change my computer or buy a cheap card creader than everything will work!!!

---

### Post by Eddy DaKillaBee on 2006-11-08
**xmux**, I have some bad news. The short story: **[COLOR="Red"]it won't happen. Not anytime soon.[/COLOR]**

The long story: I own a Toshiba P25 series laptop that also has the SD reader you have:```
02:06.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
```After trying out some of the suggestions in this thread and doing **a lot** of searching both here at the forums and elsewhere, the only thing I could find is that 1) I'm still getting nowhere with this thing and 2) apparently the drivers for this SD reader are very much closed-source and very proprietary. **No one** had any solution other than recommending people to go out and buy a USB media reader.

It sucks that we have to rely on an external card reader, but it's still cheaper than going out and buying a new laptop...;) I hope someday this issue gets fixed. Until then, I'll spend the $10 or $20 for a USB media reader and hope it just works. ^_^

If somebody **does** happen to find out how to get this thing working, I'll be more than happy to give it a try! :D

---

### Post by rulas.ram on 2006-11-22
> **leomcabral said:**
> Try this,

$ sudo modprobe tifm_sd

Insert your sd card to test it. If it works correctaly edit /etc/modules (sudo gedit /etc/modules) and add in the last line (new line) tifm_sd

I have a HP pavilion DV1015la (DV1000 series) whit a texas instrument controler(1)and the same problem, no sd read/mounting or anything else, and used the solution above adding the module tifm_ed, and worked

(1)lspci tells me that:
02:09.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller

---

### Post by Wardo on 2006-12-02
> **leomcabral said:**
> Try this,

$ sudo modprobe tifm_sd

Insert your sd card to test it. If it works correctaly edit /etc/modules (sudo gedit /etc/modules) and add in the last line (new line) tifm_sd

This has worked out for me. I'm running Edgy on a Gateway 3550GZ laptop.

Cheers!

---

### Post by kilou on 2006-12-02
I have a RICOH card reader on my laptop (MSI S260) and no proposed solution here seems to work. Both Edgy and Dapper cannot access my card reader. What can I do?

---

### Post by motang on 2006-12-08
> **leomcabral said:**
> Try this,

$ sudo modprobe tifm_sd

Insert your sd card to test it. If it works correctaly edit /etc/modules (sudo gedit /etc/modules) and add in the last line (new line) tifm_sd

Hey that worked for me thanks man, you are the best! :mrgreen:

---

### Post by rykel on 2006-12-19
i am interested in this thread as my XD Card is now detected by tifm, BUT it is NOT showing up on the desktop or anywhere else for that matter... cheers!

---

### Post by rykel on 2006-12-24
> **rykel said:**
> i am interested in this thread as my XD Card is now detected by tifm, BUT it is NOT showing up on the desktop or anywhere else for that matter... cheers!

Christmas 2006 Surprise: I am glad to let you all know that 2 of my SD cards were detected AND mounted automatically, perfectly, correctly! (see screenshot)

---

### Post by macogw on 2006-12-24
> **dbott67 said:**
> I'm afraid I'm out of ideas.  :(

By looking at your lshw output, I don't even see the SD Card Reader hardware.  There are a number of threads on the issue, but they appear to be able to detect the hardware, just not mount the card.

You'll have to keep perusing the forums (or Google at large) to see if you can find a solution.

Good luck (and if you find anything, please post a HOWTO back here).

-Dave
It's right there

description: CardBus bridge
                product: ToPIC100 PCI to Cardbus Bridge with ZV Support
                vendor: Toshiba America Info Systems
                physical id: b
                bus info: pci@02:0b.0
                version: 33
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:c2007000-c2007fff irq:3

My card uses yenta_cardbus too umm.. maybe do what I did?
modprobe tifm_7xx1
modprobe tifm_core
modprobe tifm_sd
 
see if anything happens?

---

### Post by rykel on 2006-12-24
Since my SD card can be automounted, I believe the problem lies in the driver's ability to read XD card as well... and I hope you might be able to help me... thank you!!

---

### Post by ThrobbingBrain66 on 2006-12-24
> **rykel said:**
> Since my SD card can be automounted, I believe the problem lies in the driver's ability to read XD card as well... and I hope you might be able to help me... thank you!!

In my research I found that the xD module is still in development.  For anyone looking to get their card reader working with SD and MMC, visit the link in my signature.

---

### Post by andrewtw on 2006-12-26
> **dbott67 said:**
> Yes, it may be that it's not compiled in the kernel yet.  A few things to consider:

1. 
```
sudo apt-get install ivman
```

2. 

```
sudo modprobe sd_mod
```
```
sudo modprobe scsi_mod *<-- this one appears to be loaded already.*
``` 



thank you!

my built in Ricoh card reader in HP V3016 works now!
 

:p

---

### Post by ScottMorris on 2006-12-28
I also can't get my SD card reader to work.

```
02:06.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)
```

I have followed the tutorials that I can find and still no luck.  It won't seem to mount.  There should be more support for Flash Memory as they are now really popular as they are usually easy to use and convenient.  I guess I will have to keep searching and maybe someone will come up with an answer,  It seems that TI readers work great, but not proprietary Toshiba ones.

btw i have a Satellite P10

---

### Post by eitan_a on 2006-12-29
Hey guys...i've tried everything in this thread but nothing's worked yet.

My lshw..

 *-pcmcia
                description: CardBus bridge
                product: Texas Instruments
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@08:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:dc006000-dc006fff irq:177
           *-firewire
                description: FireWire (IEEE 1394)
                product: Texas Instruments
                vendor: Texas Instruments
                physical id: 3.1
                bus info: pci@08:03.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:dc005000-dc0057ff iomemory:dc000000-dc003fff irq:177
           *-storage
                description: Mass storage controller
                product: Texas Instruments
                vendor: Texas Instruments
                physical id: 3.2
                bus info: pci@08:03.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1
                resources: iomemory:dc004000-dc004fff irq:177

My lspci

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 13)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:03.0 CardBus bridge: Texas Instruments Unknown device 8039
08:03.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
08:03.2 Mass storage controller: Texas Instruments Unknown device 803b

I'm hoping for some help here.  The laptop is a new Sony Vaio.  Thanks very much!

---

### Post by loko on 2007-01-04
i have the problem that my cardreader only works with SD-Cards but MMC-Cards are not detected.

i have this one (which can detect SD/MMC/SONY-Sticks):

```
user@user-laptop:~$ lspci -vvs 06:03
06:03.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1267
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min, 1000ns max)
        Interrupt: pin A routed to IRQ 233
        Region 0: Memory at fe8ff800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

06:03.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1267
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin B routed to IRQ 50
        Region 0: Memory at fe8ff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

06:03.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1267
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 3
        Region 0: Memory at fe8ff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

06:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1267
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 3
        Region 0: Memory at fe8fec00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

06:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1267
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 3
        Region 0: Memory at fe8fe800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
```


i know that i have this [http://www.ricoh.com/LSI/product_pcif/pcc/5c821/index.html](http://www.ricoh.com/LSI/product_pcif/pcc/5c821/index.html) chipset and ricoh says the following:
```
MMC is available when RICOH’s SD/MMC driver is used. (SDIO cannot be used at the same time)
```

is there a workaround for this problem?

---

### Post by singpolyma on 2007-02-12
I have tried everything in this thread... nothing.  lspci shows the following:

02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)

On reading this thread is seems that there is no linux driver for this card reader... I just hope there becomes one.

---

### Post by loko on 2007-02-17
i hoped that my card-reader will work in feisty, but i tested herd 4 yesterday and got disappointed.

it didn't work even with kernel 2.6.20.

what a pity

---

### Post by loko on 2007-02-20
ok,

the bug with the R5C592 chipset is described here, but no solution at this time.

[http://bugzilla.kernel.org/show_bug.cgi?id=7673]("http://bugzilla.kernel.org/show_bug.cgi?id=7673")

---

### Post by xmux on 2007-03-24
So still it doesn't work???

---

### Post by Wet Werewolf on 2007-03-27
I'm using 6.10 on an HP DV1000-based laptop and after doing the 

sudo modprobe tifm_sd

the card reader works fine.  Went ahead and added the tifm_sd line to /etc/modules and everything is peachy.

---

### Post by loko on 2007-04-10
> **xmux said:**
> So still it doesn't work???

as i can see on bugzilla, you can expect working this in kernel 2.6.21 or 22

---

### Post by loko on 2007-10-21
Finally MMC-Cards with the Rico Controller are working in Kernel 2.6.23-git16

I tested it some minutes ago and it works like expected. When building the Kernel, "Ricoh MMC disabler" has to be enabled.

---

