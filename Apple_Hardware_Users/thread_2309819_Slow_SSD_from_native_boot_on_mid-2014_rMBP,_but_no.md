---
title: "Slow SSD from native boot on mid-2014 rMBP, but not from vbox"
date: 2016-01-13
forum: Apple Hardware Users
---

### Post by satmandu on 2016-01-13
I have Ubuntu 15.10 setup on a ssd partition on my rMBP. The root partition is zfs.

When I'm natively booted into ubuntu, I'm getting very slow write speeds:


```
dd if=/dev/zero of=tempfile bs=1M count=1024 conv=fdatasync,notrunc
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 5.74565 s, 187 MB/s
```


However, when I'm booted into El Capitan, and then run ubuntu from virtualbox accessing the exact same partition in raw mode, I get much faster disk access.

```
dd if=/dev/zero of=tempfile bs=1M count=1024 conv=fdatasync,notrunc
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 0.521114 s, 2.1 GB/s
```


At first I thought this was either an issue with an older kernel or zfs, so I made sure that I was running a current kernel (kernel 4.4.0) as well as a current zfs build (v0.6.5.4-1~wily from a current zfs ppa).  Updating that software made no difference.

But booting in a virtual machine did make a difference.

So I'm assuming that this isn't a zfs issue then, but instead an issue with how linux is accessing the SSD.  Any ideas?

Is anybody else having slow disk access on one of these machines?  It is very noticeable when trying to update any software... especially when unpacking lots of small files.

---

### Post by satmandu on 2016-01-13
FYI, here's the dmesg output from a native boot for the drive:

```

[    2.774095] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.774319] ata1.00: unexpected _GTF length (8)
[    2.774429] ata1.00: ATA-8: APPLE SSD SM0512F, UXM2JA1Q, max UDMA/133
[    2.774432] ata1.00: 977105060 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.774644] ata1.00: unexpected _GTF length (8)
[    2.774797] ata1.00: configured for UDMA/133
[    2.775002] scsi 1:0:0:0: Direct-Access     ATA      APPLE SSD SM0512 JA1Q PQ: 0 ANSI: 5
[    2.775240] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    2.775274] sd 1:0:0:0: [sda] 977105060 512-byte logical blocks: (500 GB/465 GiB)
[    2.775279] sd 1:0:0:0: [sda] 4096-byte physical blocks
[    2.775539] sd 1:0:0:0: [sda] Write Protect is off
[    2.775543] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.775612] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

Here's the dmesg output from inside virtualbox for the drive:

```

[    0.946001] scsi 0:0:0:0: Direct-Access     ATA      VBOX HARDDISK    1.0  PQ: 0 ANSI: 5
[    0.947280] sd 0:0:0:0: [sda] 977105060 512-byte logical blocks: (500 GB/465 GiB)
[    0.948106] sd 0:0:0:0: [sda] Write Protect is off
[    0.948936] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.949061] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.949932] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

---

### Post by satmandu on 2016-01-13
This bug report seems to show some workarounds and a lot more discussion of the issue:

[https://bugzilla.kernel.org/show_bug.cgi?id=60731](https://bugzilla.kernel.org/show_bug.cgi?id=60731)

The workaround in the last link is to do the following:

```
Add device_nomsi=0x1600144d to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub
``` 
```
Add libata.force=noncq to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub
``` 
and then run ```
sudo update-grub
```

Only the libata.force=noncq made a difference, dropping the queue depth from 31 to 1.

Still slow. Unpacking an update is going at 500k/second.

---

