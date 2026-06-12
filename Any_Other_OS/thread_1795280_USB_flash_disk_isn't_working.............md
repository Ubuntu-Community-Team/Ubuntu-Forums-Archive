---
title: "USB flash disk isn't working............"
date: 2011-07-02
forum: Any Other OS
---

### Post by SUDOwoodo on 2011-07-02
Sup forum?

I'm running Mint 11, and I have an 8Gb USB pendrive, and it doesn't really want to work...
Before I begin, I would just like to point out that this pendrive was working with this machine, up until two days ago.

Alright, so my problem is that absolutely *nothing* happens when I put my pendrive in my computer.  Nothing shows up, nothing says that my USB device is not recognized, just nothing happens.  Though it is more than likely something very easy to fix, I do not know how to haha.
So I went into the terminal used dmesg, and this is its output:

```
[14999.764147] usb 1-3: new high speed USB device using ehci_hcd and address 7
[14999.975827] scsi7 : usb-storage 1-3:1.0
[15000.977153] scsi 7:0:0:0: Direct-Access     3SYSTEM  USB Flash Disk   1.00 PQ: 0 ANSI: 2
[15000.980626] sd 7:0:0:0: Attached scsi generic sg1 type 0
[15000.982785] sd 7:0:0:0: [sdb] 15974884 512-byte logical blocks: (8.17 GB/7.61 GiB)
[15000.983375] sd 7:0:0:0: [sdb] Write Protect is off
[15000.983394] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[15000.985762] sd 7:0:0:0: [sdb] No Caching mode page present
[15000.985782] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[15000.994045] sd 7:0:0:0: [sdb] No Caching mode page present
[15000.994068] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[15000.997701]  sdb: unknown partition table
[15001.001598] sd 7:0:0:0: [sdb] No Caching mode page present
[15001.001611] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[15001.001623] sd 7:0:0:0: [sdb] Attached SCSI removable disk

```I really don't know how to go about fixing this, so any help would be fantastic!
Also, when I try sudo fdisk /dev/sdb, it says it cannot open sdb.

Thanks in advanced!:D

---

### Post by westie457 on 2011-07-02
> **SUDOwoodo said:**
> Sup forum?

I'm running Mint 11, and I have an 8Gb USB pendrive, and it doesn't really want to work...
Before I begin, I would just like to point out that this pendrive was working with this machine, up until two days ago.

Alright, so my problem is that absolutely *nothing* happens when I put my pendrive in my computer.  Nothing shows up, nothing says that my USB device is not recognized, just nothing happens.  Though it is more than likely something very easy to fix, I do not know how to haha.
So I went into the terminal used dmesg, and this is its output:

```
[14999.764147] usb 1-3: new high speed USB device using ehci_hcd and address 7
[14999.975827] scsi7 : usb-storage 1-3:1.0
[15000.977153] scsi 7:0:0:0: Direct-Access     3SYSTEM  USB Flash Disk   1.00 PQ: 0 ANSI: 2
[15000.980626] sd 7:0:0:0: Attached scsi generic sg1 type 0
[15000.982785] sd 7:0:0:0: [sdb] 15974884 512-byte logical blocks: (8.17 GB/7.61 GiB)
[15000.983375] sd 7:0:0:0: [sdb] Write Protect is off
[15000.983394] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[15000.985762] sd 7:0:0:0: [sdb] No Caching mode page present
[15000.985782] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[15000.994045] sd 7:0:0:0: [sdb] No Caching mode page present
[15000.994068] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[15000.997701]  sdb: unknown partition table
[15001.001598] sd 7:0:0:0: [sdb] No Caching mode page present
[15001.001611] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[15001.001623] sd 7:0:0:0: [sdb] Attached SCSI removable disk

```I really don't know how to go about fixing this, so any help would be fantastic!
Also, when I try sudo fdisk /dev/sdb, it says it cannot open sdb.

Thanks in advanced!:D

Hi have you tried using Disc Utility to check the partitioning?

Chances are the mbr? of the stick has corrupted giving unknown partition table.

If there is anything important in it use testdisk to recover the partition information and possibly photorec to recover your files.

Testdisk and photorec come together in one package from the repositories.

If there is nothing of importance in it one way to format it is with Startup Disc Creator which rewrites the first few sectors to create a partition table. Or you can use Gparted to do the same thing, in Gparted just make sure you are looking at the correct drive.


Hope this helps.

---

### Post by SUDOwoodo on 2011-07-02
> **westie457 said:**
> Hi have you tried using Disc Utility to check the partitioning?

Chances are the mbr? of the stick has corrupted giving unknown partition table.

If there is anything important in it use testdisk to recover the partition information and possibly photorec to recover your files.

Testdisk and photorec come together in one package from the repositories.

If there is nothing of importance in it one way to format it is with Startup Disc Creator which rewrites the first few sectors to create a partition table. Or you can use Gparted to do the same thing, in Gparted just make sure you are looking at the correct drive.


Hope this helps.

Boy do I feel stupid now...  Hahaha.
Gparted worked like a charm, and I didn't even think about the disc utility....
Thanks for your help!

---

### Post by westie457 on 2011-07-02
> **SUDOwoodo said:**
> Boy do I feel stupid now...  Hahaha.
Gparted worked like a charm, and I didn't even think about the disc utility....
Thanks for your help!

No worries. And I still have marks in the wall from when I had the same problem:lolflag:

---

### Post by Perfect Storm on 2011-07-02
Moved to Other OS/Distro Talk.

---

