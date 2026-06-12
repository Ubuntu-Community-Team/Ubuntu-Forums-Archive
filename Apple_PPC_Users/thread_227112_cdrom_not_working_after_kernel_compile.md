---
title: "cdrom not working after kernel compile"
date: 2006-08-01
forum: Apple PPC Users
---

### Post by nosmile on 2006-08-01
Hi, two day ago, I decided to install Ubuntu Dapper on my macbook-pro.  It was working quite well but it doesn't recognize the second core of my CPU si I decided to compile the latest kernel (2.6.17.7) to get it working.  Now, it's ok but it does not recognized my cdrom...  #-o 

could you give me come way to get it working?

here is my dmesg | grep ata :
```
 BIOS-e820: 000000003f2c9000 - 000000003fe75000 (ACPI data)
 BIOS-e820: 000000003fe7d000 - 000000003feae000 (ACPI data)
 BIOS-e820: 000000003feaf000 - 000000003fec2000 (ACPI data)
 BIOS-e820: 000000003feef000 - 000000003ff00000 (ACPI data)
ACPI: SSDT (v001 APPLE   SataPri 0x00001000 INTL 0x20050309) @ 0x3febf000
ACPI: SSDT (v001 APPLE   SataSec 0x00001000 INTL 0x20050309) @ 0x3febe000
Memory: 1015708k/1032992k available (2572k kernel code, 16628k reserved, 736k data, 248k init, 115488k highmem)
libata version 1.20 loaded.
ata_piix 0000:00:1f.2: version 1.05
ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
ata_piix 0000:00:1f.2: invalid MAP value 0
ata1: SATA max UDMA/133 cmd 0x40D8 ctl 0x40F6 bmdma 0x4020 irq 50
ata2: SATA max UDMA/133 cmd 0x40D0 ctl 0x40F2 bmdma 0x4028 irq 50
ata1: dev 1 cfg 49:2f00 82:746b 83:7d09 84:6063 85:7469 86:3d09 87:6063 88:203f
ata1: dev 1 ATA-6, max UDMA/100, 195371568 sectors: LBA48
ata1: dev 1 configured for UDMA/100
scsi0 : ata_piix
ata2: SATA port has no device.
scsi1 : ata_piix
uvcvideo: Unknown symbol video_devdata

```

---

### Post by nosmile on 2006-08-01
Ok, I got it working by deselecting the option :
device drivers -> ATA/ATAPI/RMLF... ->  Include IDE/ATA-2 DISK support
 :p 
hope it could help someone...

---

### Post by moma on 2006-08-01
I always copy my old, good kernel ".config" to new kernel source.

# [COLOR="Green"]cd /usr/src/linux[/COLOR]

Take a copy of the old, good kernel ".config" file. No reason to begin from scratch.
# [COLOR="Green"]ls -l /boot/config* [/COLOR]
# [COLOR="Green"]cp /boot/config-$(uname --kernel-release)  ./.config[/COLOR]

Update the .config file with possibly new options.
# [COLOR="Green"]make oldconfig[/COLOR]

Do final kernel configuration.
# [COLOR="Green"]make menuconfig[/COLOR]

Note: I run a normal X86 PC.

---

### Post by nosmile on 2006-08-01
yes but the old ubuntu config was not booting with this kernel...  Don't know why...  (isn't it done the first time you lauch menuconfig?)

---

