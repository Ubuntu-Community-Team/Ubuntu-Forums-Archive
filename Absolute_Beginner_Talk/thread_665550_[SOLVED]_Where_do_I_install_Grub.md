---
title: "[SOLVED] Where do I install Grub"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by tad1073 on 2008-01-12
I didn't have an internet connection when I installed Ubuntu 7.10 from livecd(ordered from ubuntu) but ubuntu installed fine I just can't boot into system.

gparted set-up as follows:
/dev/ida/c0d0 0.00Bits=512Bits
HD0=/dev/sda1 8.07Gib ext3
dev/sda2 415.74MiB ext
dev/sda5 415.71MiB swap
where do I put grub and how much space do I need to allocate for it and if it is in a seperate partition how do I get it to boot?

HD1=/dev/sdb1 8.47GiB ext2 w/lost and found file on it
HD2=/dev/sdb2 8.47GiB ext2 w/lost and found file on it
how can I make this look like one 16.94GiB HD

by the way, they are 3x9.1GiB HD's

---

### Post by logos34 on 2008-01-12
I'm thinking grub installed to the mbr of one of the other disks...go into the Bios and switch the hard disk boot order.

---

### Post by tad1073 on 2008-01-12
> **logos34 said:**
> I'm thinking grub installed to the mbr of one of the other disks...go into the Bios and switch the hard disk boot order.

Boot Order as follows:
cd-rom drive
Hard drive
floppy

With hd first I get an error no operating system loaded.

---

### Post by logos34 on 2008-01-12
> **tad1073 said:**
> Boot Order as follows:
cd-rom drive
Hard drive
floppy

With hd first I get an error no operating system loaded.

That's the **device** boot order--there's a separate sub-menu for hard disks.  You have three...choose another as first.

---

### Post by tad1073 on 2008-01-12
> **logos34 said:**
> That's the **device** boot order--there's a separate sub-menu for hard disks.  You have three...choose another as first.
```
Hard Drive Controller Order
Slot 3 Compaq Wide/Ultra2 SCSI Controller
System Embedded IDE Controler
Slot 2 Compaq Smart Array 431 Controller-disabled
Boot Order
CD-Romm
Hard Drive (C:)
Floppy Drive (A:)

```

---

### Post by logos34 on 2008-01-12
> **tad1073 said:**
> ```
Hard Drive Controller Order
Slot 3 Compaq Wide/Ultra2 SCSI Controller
System Embedded IDE Controler
Slot 2 Compaq Smart Array 431 Controller-disabled

```

can't you rearrange the order of the above?

---

### Post by tad1073 on 2008-01-12
that is the order
HD0 is the Master

---

### Post by logos34 on 2008-01-12
yes, but if you're getting 'no operating system found' error, it means there's no bootloader on the drive you're trying to boot from, that's why I suggested switching the order around.  Grub bootloader does not necessarily instlal to the same disk as the ubuntu root partition is on.

add: one solution would be to disconnect the other drives and reinstall, then grub will for sure go on the ubuntu drive

---

### Post by tad1073 on 2008-01-12
I did not opt to install grub because the last time I did w/o an internet connection it just hung up at  94%

---

### Post by logos34 on 2008-01-12
> **tad1073 said:**
> I did not opt to install grub because the last time I did w/o an internet connection it just hung up at  94%

Why didn't you say so before??? 

You cannot boot an OS without a bootloader (whether grub or something else).  

Get[ Super Grub Disk]("http://supergrub.forjamari.linex.org/").  You can use that to boot ubuntu.

---

### Post by tad1073 on 2008-01-12
I just need to find the grub that comes with the live cd, any ideas on where it is at

---

