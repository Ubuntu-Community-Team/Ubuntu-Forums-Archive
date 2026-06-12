---
title: "Absolute Rookie"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by JacoC on 2008-02-20
I am very new to Linux and have installed Ubuntu 7.10 on a virtual machine on my home PC. When I first installed Ubuntu it detected my internet connection from my host (NAT connection) and I had no problem connecting to the internet through the virtual machine until I updated ubuntu with the updates as per the update manager.

I have tried endlessly to reinstate the connection but have had no success. I followed suggestions from the documentation but this does not help either...my last resort...this forum.

Is there anyone out there that will be able to assist me?

---

### Post by jan quark on 2008-02-20
sure we will assist you

but as a side note

a virtualization will never be as stable and safe as the installation to the drive

please post the results of the following terminal commands
```

iwconfig
```

```
ifconfig
```
```

sudo iwlist scan
```

```
lspci
```
```

sudo lshw -C network
```

---

### Post by JacoC on 2008-02-20
**Code: iwconfig**

eth0      no wireless extensions.


**Code: ifconfig**

eth0   Link encap:Ethernet  HWaddr 00:0C:29:5D:70:3E  
          inet addr:XXX.XXX.XXX.XXX  Bcast:XXX.XXX.XXX.XXX  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5724 (5.5 KB)  TX bytes:5605 (5.4 KB)
          Interrupt:16 Base address:0x2024 

***[COLOR="Red"](I have omitted the IP address)[/COLOR]***

**Code: sudo iwlist scan**

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


**Code: lspci**

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0f.0 VGA compatible controller: VMware Inc [VMware SVGA II] PCI Display Adapter
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
00:11.0 PCI bridge: VMware Inc Unknown device 0790 (rev 02)
02:00.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
02:01.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
02:02.0 USB Controller: VMware Inc Unknown device 0770

**Code: sudo lshw -c network**

Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status

---

