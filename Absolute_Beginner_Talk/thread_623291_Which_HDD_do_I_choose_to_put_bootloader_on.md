---
title: "Which HDD do I choose to put bootloader on?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Marfish on 2007-11-25
I am installing ubuntu 7.10 on an external hdd. I already installed before, but that ended with my computer not being able to boot without the external hdd plugged in. So I was wondering which hdd I should choose when manipulating the bootloader in installation. It currently sais (hd1), so that would be my internal, but I also have a recovery hd, would this effect anything, or should I go with (hd2)? This is on my laptop. Drive c: Local disk, drive d: recovery. Then theres my external, which no longer shows up since I formatted it in the last installation.

---

### Post by njparton on 2007-11-25
When I install on a desktop, I always unplug all other drives so that the bootloader doesn't inadvertantly get installed on the wrong drive (and I use the bootloader in the BIOS to select which drive to boot).

That may not be so easy for you, but try unplugging your other drives and then it will only have 1 drive to choose from?

---

### Post by Marfish on 2007-11-25
Hmm, both the recovery and the local are internal. Thanks anyway, any other suggestions though?

---

### Post by Marfish on 2007-11-25
,

---

### Post by Marfish on 2007-11-25
I just realized, could my drive d: be a partition on my internal drive with the local drive? Does that change anything?

---

### Post by Marfish on 2007-11-25
The partition tables of the following devices are changed:
 SCSI8 (0,0,0) (sdb)

The following partitions are going to be formatted:
 partition #1 of SCSI8 (0,0,0) (sdb) as ext3
 partition #5 of SCSI8 (0,0,0) (sdb) as swap

Heres the final stage of the installation, and the bootloader apparently wants to install itself on (hd0). What would be the name of my external drive?

---

