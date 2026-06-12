---
title: "need a driver"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-12-05
Hi

I'm looking for a a rtl8139 driver for installing an ethernet card (2.16 kernel in draper). I've been searching with google, but in vain.

Any hint? Thanx

---

### Post by Freiburg05 on 2006-12-05
There is a possible solution in the spanish ubuntu forums to install these ethernet cards, I don't know if you can understad it but may be useful.  

[http://www.ubuntu-es.org/index.php?q=node/26884](http://www.ubuntu-es.org/index.php?q=node/26884)

---

### Post by Bachstelze on 2006-12-05
Drivers are available from Realtek. They're said to work only on 2.4 kernels but I think you should be OK on 2.6 too.

---

### Post by steve.horsley on 2006-12-05
Have you tried the card already? My last PC had an rtl8139 Ethernet card and it worked out of the box with both Mandrake, Ububtu Hoary and Ubuntu Breezy. I doubt that the driver has been removed from later kernels.

---

### Post by hotbrainz on 2006-12-05
for translation from spanish you can use:

[http://babelfish.altavista.com/]("http://babelfish.altavista.com/")

cheers.

---

### Post by helphope on 2006-12-05
Thanks to everybody for replying.


> **HymnToLife said:**
> Drivers are available from Realtek. They're said to work only on 2.4 kernels but I think you should be OK on 2.6 too.

Installing the driver I've got this message, from which I can understand - if Im not wrong - that I've installed the wrong driver, that is the one for 2.4 kernel.
That's why i'm looking for the driver suitable for 2.6 kernel

Citazione:
*****************************
sc92031.o built for 2.6.15-26-386
SMP Disabled
*****************************

In file included from /lib/modules/2.6.15-26-386/build/include/linux/irq.h:22,
from /lib/modules/2.6.15-26-386/build/include/asm/hardirq.h:6,
from /lib/modules/2.6.15-26-386/build/include/linux/hardirq.h:7,
from /lib/modules/2.6.15-26-386/build/include/linux/interrupt.h:11,
from /lib/modules/2.6.15-26-386/build/include/linux/rcuref.h:36,
from /lib/modules/2.6.15-26-386/build/include/linux/fs.h:12,
from /lib/modules/2.6.15-26-386/build/include/linux/mm.h:15,
from /lib/modules/2.6.15-26-386/build/include/asm/pci.h:7,
from /lib/modules/2.6.15-26-386/build/include/linux/pci.h:612,
from sc92031.c:19:
/lib/modules/2.6.15-26-386/build/include/asm/irq.h:16:25: error: irq_vectors.h: No such file or directory
In file included from /lib/modules/2.6.15-26-386/build/include/asm/hardirq.h:6,
from /lib/modules/2.6.15-26-386/build/include/linux/hardirq.h:7,
from /lib/modules/2.6.15-26-386/build/include/linux/interrupt.h:11,
from /lib/modules/2.6.15-26-386/build/include/linux/rcuref.h:36,
from /lib/modules/2.6.15-26-386/build/include/linux/fs.h:12,
from /lib/modules/2.6.15-26-386/build/include/linux/mm.h:15,
from /lib/modules/2.6.15-26-386/build/include/asm/pci.h:7,
from /lib/modules/2.6.15-26-386/build/include/linux/pci.h:612,
from sc92031.c:19:
/lib/modules/2.6.15-26-386/build/include/linux/irq.h:85: error: &#8216;NR_IRQS&#8217; undeclared here (not in a function)
In file included from /lib/modules/2.6.15-26-386/build/include/linux/irq.h:94,
from /lib/modules/2.6.15-26-386/build/include/asm/hardirq.h:6,
from /lib/modules/2.6.15-26-386/build/include/linux/hardirq.h:7,
from /lib/modules/2.6.15-26-386/build/include/linux/interrupt.h:11,
from /lib/modules/2.6.15-26-386/build/include/linux/rcuref.h:36,
from /lib/modules/2.6.15-26-386/build/include/linux/fs.h:12,
from /lib/modules/2.6.15-26-386/build/include/linux/mm.h:15,
from /lib/modules/2.6.15-26-386/build/include/asm/pci.h:7,
from /lib/modules/2.6.15-26-386/build/include/linux/pci.h:612,
from sc92031.c:19:
/lib/modules/2.6.15-26-386/build/include/asm/hw_irq.h:30: error: &#8216;NR_IRQ_VECTORS&#8217; undeclared here (not in a function)
In file included from /lib/modules/2.6.15-26-386/build/include/linux/if_ether.h:109,
from /lib/modules/2.6.15-26-386/build/include/linux/netdevice.h:29,
from sc92031.c:22:
/lib/modules/2.6.15-26-386/build/include/linux/skbuff.h: In function &#8216;skb_add_data&#8217;:
/lib/modules/2.6.15-26-386/build/include/linux/skbuff.h:1128: warning: pointer targets in passing argument 1 of &#8216;csum_and_copy_from_user&#8217; differ in signedness
sc92031.c:103:40: error: missing binary operator before token "("
sc92031.c: In function &#8216;silan_probe&#8217;:
sc92031.c:410: error: &#8216;struct pci_dev&#8217; has no member named &#8216;slot_name&#8217;
sc92031.c:426: error: &#8216;struct pci_dev&#8217; has no member named &#8216;slot_name&#8217;
sc92031.c:457: error: &#8216;struct pci_dev&#8217; has no member named &#8216;slot_name&#8217;
sc92031.c:464: error: &#8216;struct pci_dev&#8217; has no member named &#8216;slot_name&#8217;
sc92031.c: In function &#8216;silan_open&#8217;:
sc92031.c:923: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
sc92031.c: In function &#8216;silan_ethtool_ioctl&#8217;:
sc92031.c:1804: error: &#8216;struct pci_dev&#8217; has no member named &#8216;slot_name&#8217;
sc92031.c:1814: error: &#8216;np&#8217; undeclared (first use in this function)
sc92031.c:1814: error: (Each undeclared identifier is reported only once
sc92031.c:1814: error: for each function it appears in.)
sc92031.c:1866:40: error: missing binary operator before token "("
sc92031.c: At top level:
sc92031.c:1976: warning: initialization from incompatible pointer type
sc92031.c: In function &#8216;silan_init_module&#8217;:
sc92031.c:1992: warning: pointer targets in assignment differ in signedness
sc92031.c:1995: warning: pointer targets in assignment differ in signedness
sc92031.c:1998: warning: pointer targets in assignment differ in signedness
sc92031.c:2001: warning: pointer targets in assignment differ in signedness
sc92031.c:2004: warning: pointer targets in assignment differ in signedness
make: *** [sc92031.o] Error 1

---

### Post by yota on 2006-12-05
The module for realtek 8139 is already included in the kernel (as steve already said)
> 
yota@linbook:/lib/modules/2.6.15-27-686$ modinfo 8139too
filename:       /lib/modules/2.6.15-27-686/kernel/drivers/net/8139too.ko
author:         Jeff Garzik <jgarzik@pobox.com>
description:    RealTek RTL-8139 Fast Ethernet driver
license:        GPL
version:        0.9.27
vermagic:       2.6.15-27-686 SMP preempt 686 gcc-4.0


Are you having issues with it? Why do you think you need a driver?

Hope this helps!

---

### Post by helphope on 2006-12-05
> **yota said:**
> The module for realtek 8139 is already included in the kernel (as steve already said)
Are you having issues with it? Why do you think you need a driver?



This helps! But I don't understand how.
The card is not detected and when I compile the driver of the card it gives me back the error I posted above and which I get k at the point 5 of the readme.txt I found in the floppy with the card

>   5) Compile the driver source files and it will generate sc92031.o, and    copy it to correct driver installation path (The installation directory   is different in different kernel versions. In 2.4.x kernel, the path is     /lib/modules/KERNEL_VERSION/kernel/drivers/net/, and in 2.2.x kernel,     the path is /lib/modules/KERNEL_VERSION/net/)
       # make install

    6) Check configuration file (/etc/modules.conf or /etc/conf.modules,it
       depend on your Linux distribution) for loading kernel modules. Make sure     there is the following content in the configuration file, where # is  interface number : alias eth# sc92031
 
    7) Reboot now:
        shutdown -r now 

---

### Post by helphope on 2006-12-05
> filename: /lib/modules/2.6.15-27-686/kernel/drivers/net/28169too.ko
/lib/modules/2.6.15-27-686/kernel/drivers/net/2100too.ko


8139too.ko is missing
:confused:

---

### Post by yota on 2006-12-06
> 
yota@linbook:~$ dpkg -S 8139too.ko
linux-image-2.6.15-27-686: /lib/modules/2.6.15-27-686/kernel/drivers/net/8139too.ko

the needed module is in the 'linux-image-*' package, if the file is missing (something or someone has deleted it) reinstall the kernel package with:
```

sudo aptitude reinstall linux-image-2.6.15-27-686

```
If you are using a different kernel version, please update the command accordingly.

Once the file is in place you can load the module by issuing:
```

sudo modprobe 8139too

```
and watch the kernel messages with:
```

dmesg

```
you can get a list of all available network interfaces with:
```

ifconfig -a

```

Let me know if you can see the interface listed after reinstalling the kernel package and loading the module.

---

### Post by helphope on 2006-12-06
Hi, thanks for replying

 ```
dpkg -S 8139too.ko
linux-image-2.6.15-26-386: /lib/modules/2.6.15-26-386/kernel/drivers/net/8139too.ko
```

```

dmesg
It gives me back 5 pages of report. Just post these few lines (trying to guess ...)
[17179610.500000] **** SET: Misaligned resource pointer: c558c322 Type 07 Len 0
[17179610.504000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179610.504000] PCI: setting IRQ 11 as level-triggered
[17179610.504000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11

```

```

ifconfig -a
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4328 (4.2 KiB)  TX bytes:4328 (4.2 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```


:confused: :confused:

---

### Post by yota on 2006-12-06
Hi helphope,

apparently you have missed some points in my last post; no worries, I'll go over again trying to clarify better.
From what I can see you are using the linux-image-2.6.15-26-386 kernel (you can double-check with 'uname -a'), and the driver for your card is already found at this path: /lib/modules/2.6.15-26-386/kernel/drivers/net/8139too.ko
So the driver is present on your system (please check) and you don't need to compile anything from realtek, we have just to enable it and see if it works. Then we can see why it's not automatically loaded by the system.

You can load the driver with
```

sudo modprobe 8139too

```
Once you do that the last lines in 'dmesg' will show you how the module loading went (and if there were errors).
```

sudo lsmod

```
lists the already loaded modules, please check if 8139too is in the list.
Finally 'ifconfig -a' should show an 'eth0' peripheral that wasn't present before.

Let me know how it goes, or ask me if something needs a better explanation.

---

### Post by helphope on 2006-12-06
uname -a confirms the 2.6.15-26-386 kernel 
I've got  /lib/modules/2.6.15-26-386/kernel/drivers/net/8139too.ko
```

sudo modprobe 8139too

``` replies me nothing.
Once you do that the last lines in 'dmesg' will show you how the module loading went (and if there were errors).
```

sudo lsmod

``` replies me

 sudo lsmod
Module                  Size  Used by
8139too                26880  0
mii                     5888  1 8139too

(Just the first two lines)

```
dmesg
```
8139t00 fst ethernet driver 0.9.27 (last line)

 ```
ifconfig -a
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

 ```
ifconfig eth0 
```

error while getting interfaqce flags: no such device

 ```
pppoeconf 
```
sorry. No working ethernet card could be found. ...




 Everything started in generating the sc92031.o file which I failed and gives me back the message SMP DISABLED ...

---

### Post by yota on 2006-12-06
> **helphope said:**
> 
sudo lsmod
[/code] replies me

 sudo lsmod
Module                  Size  Used by
8139too                26880  0
mii                     5888  1 8139too

(Just the first two lines)

```
dmesg
```
8139t00 fst ethernet driver 0.9.27 (last line)

Looking at dmesg, seems that the module loads fine, but it doesn't detect any card...
Could you please post the output of:
```

lspci

```
So we can see the details about the card, chip revision and so on...

---

### Post by helphope on 2006-12-07
Thanks for replying
> 0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8605 [ProSavage PM133] (rev 8 1)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8605 [PM133 AGP]
0000:00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (r ev 22)
0000:00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 10)
0000:00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 10)
0000:00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 10)
0000:00:04.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (r ev 30)
0000:00:0e.0 Ethernet controller: Unknown device 1904:2031 (rev 01)
0000:00:0f.0 Multimedia audio controller: Yamaha Corporation YMF-724F [DS-1 Audi o Controller] (rev 03)
0000:00:10.0 Communication controller: Rockwell International HCF 56k Data/Fax M odem (rev 01)
0000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. G400/G450 (rev 04)


As far as I can understand there isn't any Ethernet card detected. Is that possible that driver source files are for 2.4 kernel and they can't be compiled in 2.6 kernel?:confused:

---

### Post by steve.horsley on 2006-12-07
Well, an Ethernet Controller has been spotted but not recognised. Before Yoda gets back, can you see if you can get more info on it with **sudo lshw** and **sudo lspci -vv**?

---

### Post by helphope on 2006-12-07
Thnxs.So many things, anyway I post them al the same
sudo lshw>   description: Tower Computer
    product: System Name
    vendor: CdcPointSpa
    version: System Version
    serial: SYS-1234567890
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=tower
  *-core
       description: Motherboard
       product: CUV4X
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.xx
       serial: xxxxxxxxxxx
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: ASUS CUV4X ACPI BIOS Revision 1005 (06/19/2000)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi agp
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.3
          slot: PGA 370
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 256KB
             capacity: 256KB
             capabilities: pipeline-burst synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 128MB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 128MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
             slot: DIMM 2
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: DIMM 3
     *-pci:0
          description: Host bridge
          product: VT8605 [ProSavage PM133]
          vendor: VIA Technologies, Inc.
          physical id: e4000000
          bus info: pci@00:00.0
          version: 81
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e4000000-e7ffffff
        *-pci
             description: PCI bridge
             product: VT8605 [PM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: G400/G450
                vendor: Matrox Graphics, Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 04
                size: 32MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=matrox_w1
                resources: iomemory:e2000000-e3ffffff iomemory:e1000000-e1003fff iomemory:e0800000-e0ffffff irq:11
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 4
             bus info: pci@00:04.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 4.1
             bus info: pci@00:04.1
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:d800-d80f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD205BA
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 16.13M16
                   serial: WD-WM9491057369
                   size: 19GB
                   capacity: 19GB
                   capabilities: ata dma lba iordy smart pm partitioned partitioned:dos
                   configuration: mode=udma4 smart=on
                 *-volume:0
                      description: W95 FAT32 (LBA) partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 8965MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 10GB
                      capabilities: primary
                 *-volume:2
                      description: Extended partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 360MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   description: CD-R/CD-RW writer
                   product: RW-241040
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.00
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
              *-cdrom:1
                   description: DVD reader
                   product: DVDROM 10X
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: 40
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdd
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 4.2
             bus info: pci@00:04.2
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d400-d41f irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 4.3
             bus info: pci@00:04.3
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d000-d01f irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-network UNCLAIMED
             description: Ethernet controller
             physical id: e
             bus info: pci@00:0e.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:e0000000-e00000ff ioport:b800-b8ff irq:10
        *-multimedia
             description: Multimedia audio controller
             product: YMF-724F [DS-1 Audio Controller]
             vendor: Yamaha Corporation
             physical id: f
             bus info: pci@00:0f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Yamaha DS-XG PCI
             resources: iomemory:df800000-df807fff irq:5
        *-communication UNCLAIMED
             description: Communication controller
             product: HCF 56k Data/Fax Modem
             vendor: Rockwell International
             physical id: 10
             bus info: pci@00:10.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:df000000-df00ffff ioport:b400-b407 irq:9
     *-pci:1
          description: Host bridge
          product: VT82C686 [Apollo Super ACPI]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@00:04.4
          version: 30
          width: 32 bits
          clock: 33MHz

sudo lspci -vv

> 0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8605 [ProSavage PM133] (rev 81)
        Subsystem: ASUSTeK Computer Inc. CUV4X mainboard
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Region 0: Memory at e4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [a0] AGP version 2.0
                Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2,x4
                Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x1        Capabilities: [c0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8605 [PM133 AGP] (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR+
        Latency: 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: e0800000-e1dfffff
        Prefetchable memory behind bridge: e1f00000-e3ffffff
        BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
        Subsystem: ASUSTeK Computer Inc. CUV4X mainboard
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

0000:00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10) (prog-if 8a [Master SecP PriP])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Region 4: I/O ports at d800 [size=16]
        Capabilities: [c0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin D routed to IRQ 9
        Region 4: I/O ports at d400 [size=32]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin D routed to IRQ 9
        Region 4: I/O ports at d000 [size=32]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:04.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin ? routed to IRQ 9
        Capabilities: [68] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:0e.0 Ethernet controller: Unknown device 1904:2031 (rev 01)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (5000ns min, 10000ns max)
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at e0000000 (32-bit, non-prefetchable) [size=256]
        Region 1: I/O ports at b800 [size=256]
        Expansion ROM at 10000000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Vital Product Data

0000:00:0f.0 Multimedia audio controller: Yamaha Corporation YMF-724F [DS-1 Audio Controller] (rev 03)
        Subsystem: Yamaha Corporation DS-XG PCI Audio CODEC
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+
        Latency: 32 (1250ns min, 6250ns max)
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at df800000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: [50] Power Management version 1
                Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:10.0 Communication controller: Rockwell International HCF 56k Data/Fax Modem (rev 01)
        Subsystem: Rockwell International HCF 56k Data/Fax Modem
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 9
        Region 0: Memory at df000000 (32-bit, non-prefetchable) [size=64K]
        Region 1: I/O ports at b400 [size=8]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2- AuxCurrent=0mA PME(D0-,D1+,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. G400/G450 (rev 04) (prog-if 00 [VGA])
        Subsystem: Matrox Graphics, Inc. Millennium G400 MAX/Dual Head 32Mb
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (4000ns min, 8000ns max), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at e2000000 (32-bit, prefetchable) [size=32M]
        Region 1: Memory at e1000000 (32-bit, non-prefetchable) [size=16K]
        Region 2: Memory at e0800000 (32-bit, non-prefetchable) [size=8M]
        Expansion ROM at e1ff0000 [disabled] [size=64K]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [f0] AGP version 2.0
                Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2,x4
                Command: RQ=32 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x1

:-# :confused:

---

### Post by yota on 2006-12-07
> **helphope said:**
> 
Ethernet controller: Unknown device 1904:2031 (rev 01)
Here we are... Unfortunately the ethernet card is  not recognized by the system, cause it's an unsupported variant of the 8139 chipset.

AFAIK there are no drivers for kernel 2.6, and no official support. I'm afraid that the only chance to get it working on linux is by using the windows driver with ndiswrapper like at:
[http://forums.fedoraforum.org/forum/showthread.php?t=87760&page=3](http://forums.fedoraforum.org/forum/showthread.php?t=87760&page=3)
 
But there are also evidences of  people that are getting their board replaced as :
[http://www.linuxquestions.org/questions/showthread.php?t=410414](http://www.linuxquestions.org/questions/showthread.php?t=410414)  

As bottom line I think that hardware manufacturers that do not cooperate with community to ensure that proper drivers are available are to be avoided if possible. So I encourage you to switch to one of the many ethernet adapter fully supported under linux.

I'm sorry that we can't find a full solution to your problem.

--EDIT: later we have found that it's not an unsupported variant, but a total different chip: see next posts.

---

### Post by helphope on 2006-12-07
> **yota said:**
> :D 

As bottom line I think that hardware manufacturers that do not cooperate with community to ensure that proper drivers are available are to be avoided if possible. So I encourage you to switch to one of the many ethernet adapter fully supported under linux.

I'm sorry that we can't find a full solution to your problem.

Thanks you a lot!
Just one more question: is there a way I can be sure that any device (an ethernet card, a printer or any kind of external device, ...) is supported under linux? Is there a place I can have a check? Just in case I'l buy something else.

Thanks a lot again.:)

---

### Post by yota on 2006-12-07
> 
Just one more question: is there a way I can be sure that any device (an ethernet card, a printer or any kind of external device, ...) is supported under linux?


Sure! You can have a look at:
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)
and more specifically to:
[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards)

(with some irony you can see there that RTL-8139/8139C/8139C+ are supported... :( )

Another resource about compatibility with linux in general is this:
[http://www.linuxcompatible.org/compatibility.html](http://www.linuxcompatible.org/compatibility.html)

And don't forget that if you want to have more in-depth information you can also download the kernel sources (linux-source package) and look in the 'Documentation' folder, where are stored many comments from the devs, hardware modules included.

---

### Post by helphope on 2006-12-08
thanks and my compliments

---

### Post by foolosophy on 2006-12-09
I think I have the same problem. My guess is that the card is a fake: it´s not a Realtek, but a Silan. The model is SC92031, as it says in the driver they provide (which is only for 2.2 & 2.4 kernels). So I´m also stuck. Please post if you find a solution.
Here are some relevant links:
[http://www.linuxquestions.org/questions/showthread.php?t=441115](http://www.linuxquestions.org/questions/showthread.php?t=441115)
[http://kernelyogi.livejournal.com/](http://kernelyogi.livejournal.com/)
Thanks,

Pablo

---

### Post by helphope on 2006-12-09
:confused: 

I wish I could. maybe I've got the module but I haven't tried it yet. Inside there is a readme.txt;let me know

---

### Post by yota on 2006-12-12
FYI I managed to test a NIC based on a realtek 8139D chip ("RTL8139D" id upon it), and it worked perfectly with the 8139too driver.

By further readings of posts in other forums I believe that foolosophy has got to the point: some cards are sold as 8139 but are just fakes and use another unsupported chip instead.

---

### Post by helphope on 2006-12-13
> **yota said:**
> FYI I managed to test a NIC based on a realtek 8139D chip ("RTL8139D" id upon it), and it worked perfectly with the 8139too driver.


What I can understand is that there is no way out to the problem. :confused:

---

