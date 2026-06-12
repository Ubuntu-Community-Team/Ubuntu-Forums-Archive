---
title: "trying to understand dmesg"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by theorem_hunter on 2007-03-23
hi, i am trying to understand everything that comes out of dmesg so i can trouble shoot my pc...

what do the following mean?

[LIST=1]
[*]Aperture from northbridge cpu 0 too small (32 MB)
[*]SELinux:  Disabled at boot.
[*]audit: initializing netlink socket (disabled)
[*]RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[*]ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[*]ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[*]GSI 16 sharing vector 0xD9 and IRQ 16
[*]ata1: SATA link down (SStatus 0)
[*]NFORCE-CK804: not 100% native mode: will probe irqs later
[*]NFORCE-CK804: BIOS didn't set cable bits correctly. Enabling workaround. >>> this worries me
[*]forcedeth: using HIGHDMA ???
[*]input: PC Speaker as /class/input/input1
[*]bttv0: i2c: checking for MSP34xx @ 0x80... not found
[*]ts: Compaq touchscreen protocol output
[*]drivers/usb/serial/ftdi_sio.c: v1.4.3:USB FTDI Serial Converters Driver
[*]md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[*]ibm_acpi: ec object not found
[*][drm] Setting GART location based on new memory map
[*]lo: Disabled Privacy Extensions
[*]bttv0: timeout: drop=65 irq=22617/22617, risc=1f390024, bits: HSYNC OFLOW FDSR
[/LIST]

thanks

---

### Post by gimfred on 2007-03-24
1. Seems to be a problem with your bios from what I gathered from google. This thread seems to have found out how to fix it, but I don't know what IOMMU_DEBUG is.
[IOMMU_DEBUG to Y]("http://linux.derkeiler.com/Mailing-Lists/Kernel/2005-10/6599.html")

2. SELinux is Security Enhanced Linux. see:
[http://www.nsa.gov/selinux/]("http://www.nsa.gov/selinux/"),
[The UnOfficial SELinux FAQ]("http://www.crypt.gen.nz/selinux/faq.html") and
[https://wiki.ubuntu.com/SELinux]("https://wiki.ubuntu.com/SELinux")

So far all I have done is google your . points. I can continue at a later date, and/or you could try finding out about them too. I'm not trying to growl at you, but sooner or later your feet will come off the bottom of the pool. :) 

If you are still having trouble, just say so and I'll be glad to help if I can.

---

