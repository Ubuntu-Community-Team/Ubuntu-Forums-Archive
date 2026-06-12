---
title: "Cannot mount local filesystems on boot"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-02-09
I've searched the forums and can't find a definitive solution to this error.
After booting I can type "mount -a" from the terminal which mounts the 3 XP partitions.  But why not on boot?
Also, I would like to copy some of the files from the XP partitions to the Linux partitions...is there a best way to go about that?

As always, thanks for your help.

---

### Post by Mustard on 2006-02-09
Have you looked through your logs for what errors might be occuring during startup?

---

### Post by Cousindaddy on 2006-02-09
Here is an excerpt from my syslog taken right after boot. I believe the system is configuring the drives at this point: 

> localhost kernel No module symbols loaded - kernel modules not enabled. 
localhost kernel apability LSM initialized
localhost kernel [4294672.078000] NET: Registered protocol family 1
localhost kernel [4294672.091000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
localhost kernel [4294672.091000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
localhost kernel [4294672.091000] ACPI: bus type ide registered
localhost kernel [4294672.097000] ICH5: IDE controller at PCI slot 0000:00:1f.1
localhost kernel [4294672.097000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
localhost kernel [4294672.097000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
localhost kernel [4294672.097000] ICH5: chipset revision 2
localhost kernel [4294672.097000] ICH5: not 100%% native mode: will probe irqs later
localhost kernel [4294672.097000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
localhost kernel [4294672.097000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
localhost kernel [4294672.097000] Probing IDE interface ide0...
localhost kernel [4294672.361000] hda: Maxtor 6Y120L0, ATA DISK drive
localhost kernel [4294672.973000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
localhost kernel [4294672.973000] Probing IDE interface ide1...
localhost kernel [4294673.645000] hdc: SONY DVD-ROM DDU1612, ATAPI CD/DVD-ROM drive
localhost kernel [4294674.359000] hdd: LITE-ON LTR-52246S, ATAPI CD/DVD-ROM drive
localhost kernel [4294674.410000] ide1 at 0x170-0x177,0x376 on irq 15
localhost kernel [4294674.410000] Probing IDE interface ide2...
localhost kernel [4294674.923000] Probing IDE interface ide3...
localhost kernel [4294675.435000] Probing IDE interface ide4...
localhost kernel [4294675.947000] Probing IDE interface ide5...
localhost kernel [4294676.462000] hda: max request size: 128KiB
localhost kernel [4294676.474000] hda: 240121728 sectors (122942 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
localhost kernel [4294676.474000] hda: cache flushes supported
localhost kernel [4294676.474000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 > p3 p4
localhost kernel [4294676.505000] hdc: ATAPI 40X DVD-ROM drive, 512kB Cache
localhost kernel [4294676.505000] Uniform CD-ROM driver Revision: 3.20
localhost kernel [4294676.521000] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
localhost kernel [4294676.911000] Attempting manual resume
localhost kernel [4294676.918000] swsusp: Suspend partition has wrong signature?

---

### Post by taurus on 2006-02-09
What does your /etc/fstab look like then?

---

### Post by Cousindaddy on 2006-02-10
Here is my /etc/fstab:

> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1    Desktop/c: ntfs  nls=utf8,umask=0222 0    0
/dev/hda5    Desktop/d: ntfs  nls=utf8,umask=0222 0    0
/dev/hda3    Desktop/e: ntfs  nls=utf8,umask=0222 0    0


---

### Post by tokyovigilante on 2006-02-10
When you boot, the system cannot resolve Desktop/C: and so on to physical mount points on the disk. I assume these are within your /home directory. 

When you are logged in, and issue a mount -a command, you are within your home directory and the system can resolve the paths.

Long story short, add /home/<username>/ to your /etc/fstab mountpoints and they should load on boot.

Convention is to put mountpoints within /media so they are accessible at boot and to any user of your computer.

---

