---
title: "Access NTFS partition problem"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by charr on 2006-08-19
Hi, I installed Ubuntu 6.06 yesterday, and it went off without a hitch.  Now, my only problem is that I want to access my NTFS partition from linux (my windows drivers are corrupted for the 10000th time), and cannot.  Is the partition corrupt or I just cannot access it?  The mount exists, yet Ubuntu claims it is empty.

---

### Post by taurus on 2006-08-19
Do you mount your NTFS thru /etc/fstab?  What does your /etc/fstab look like then?

```
more /etc/fstab
```
Also, what is the output of this command, from a terminal?

```
df -h
```

---

### Post by charr on 2006-08-19
```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.6G  2.5G  6.6G  28% /
varrun                252M   80K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  172K  251M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  234M   8% /lib/modules/2.6.15-26-686/volatile
/dev/sdb1             122M     0  122M   0% /media/128CF1

$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/WINXP    ntfs    defaults,nls=utf8,umask=007,gid=46 0
   1
/dev/sda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
I mounted the NTFS as /media/WINXP.  THe 128CF1 is a compact flash card in my printer.

My linux partition is 10GB, swap is 320MB.  My NTFS partition is 101GB

---

### Post by taurus on 2006-08-19
Well, apparently, /dev/sda1 is not mounted because it's not listed in "df -h" at all!  What happens if you run this from a promtp?

```

sudo mount -t ntfs /dev/sda1 /media/WINXP

```
p.s.  Make sure you have /media/WINXP first!!!

---

### Post by charr on 2006-08-19
Error output:
```

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by taurus on 2006-08-19
Are you sure your XP is on /dev/sda1???  What does dmesg have to say about your XP?

```
dmesg | more
```

---

### Post by charr on 2006-08-19
```

[17179569.184000] Linux version 2.6.15-26-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001ff30000 (usable)
[17179569.184000]  BIOS-e820: 000000001ff30000 - 000000001ff40000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001ff40000 - 000000001fff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 130864
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126768 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f9e30
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x11000306 MSFT 0x00000097) @ 0x1ff30000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x11000306 MSFT 0x00000097) @ 0x1ff30200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x11000306 MSFT 0x00000097) @ 0x1ff30390
[17179569.184000] ACPI: OEMB (v001 A M I  OEMBIOS  0x11000306 MSFT 0x00000097) @ 0x1ff40040
[17179569.184000] ACPI: DSDT (v001  P4C81 P4C81093 0x00000093 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:2 APIC version 20
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfb80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 3007.343 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource

```

Both partitions are on an SCSI hard drive.
System:
Pentium 4 3.0GHz, HT enabled
512 MB DDR1
120GB SCSI Hard drive
Geforce 4 FX 5200 (128 MB)

---

### Post by taurus on 2006-08-19
Is your drive an IDE or a SATA?  Right now, it is a SATA--/dev/sda1!

---

### Post by charr on 2006-08-19
I edited the post above, it is an SCSI drive.

---

### Post by taurus on 2006-08-19
And I assume XP is on the first drive, /dev/sda1, while Ubuntu is on the second drive, /dev/sdb?  Right now, can you boot your XP from /dev/sda1 at all?

---

### Post by charr on 2006-08-19
Currently XP is busted from driver corruption, but it boots partly.  Ubuntu is also on /dev/sda (it is sda2).  A 128 MB compact flash card is sdb.

---

### Post by taurus on 2006-08-19
Okay, what is the output of this then?

```

sudo fdisk -l

```

---

### Post by charr on 2006-08-19
Ubutunu boots when the system is turned on

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13288   106735828+   7  HPFS/NTFS
/dev/sda2           13289       14552    10153080   83  Linux
/dev/sda3           14553       14593      329332+  82  Linux swap / Solaris

Disk /dev/sdb: 128 MB, 128188416 bytes
8 heads, 32 sectors/track, 978 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         977      125040    6  FAT16

```

---

### Post by taurus on 2006-08-19
```

sudo mount /dev/sda1 /media/WINXP
-or-
sudo mount -t ntfs /dev/sda1 /media/WINXP

```
And if you still get the same error message, maybe the /dev/sda1 is so corrupted that Ubuntu can't read it to mount it!!!  ](*,)

---

### Post by charr on 2006-08-19
Niether worked.  Going to check to see if the partition was corrupted.  Thanks for the immense ammount of help :)

---

