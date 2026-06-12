---
title: "Cannot see SATA hard drives"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by nedsbeds on 2006-11-18
Hi,
I am having trouble seeing/formatting/mounting some new SATA drives.
I am using a Silicon images sil 3512 SATA pci card and have two 400GB samsung drives attached to it. 

I can see the pci card in the device manager and it has two SCSI host adaptors listed but I cannot seem to find any reference to the actual drives. (gparted only shows the two ide drives) 
The drives appear in the sata cards bios.

I am not attempting to set these up in a raid array, and they have not been formatted yet. 

I have dapper on here at the moment but plan to upgrade it to edgy soon.

Thanks in advance for any help

Nick

---

### Post by taurus on 2006-11-18
What is the output of this command from a terminal, Applications -> Accessories -> Terminal?

```
sudo fdisk -l
```

---

### Post by nedsbeds on 2006-11-19
Hi,
the output is

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9565    76830831   83  Linux
/dev/hda2            9566        9729     1317330    5  Extended
/dev/hda5            9566        9729     1317298+  82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4998    40146403+  83  Linux


Those being two ide drives that are in the computer

Thanks

Nick

---

### Post by ReaderRat on 2006-11-19
I had PATA (IDE) drives with SATA drives - no RAID - and I had to set the SATA drives to be used as IDE drives in the BIOS. Do you have that option?

---

### Post by nedsbeds on 2006-11-20
It is a pci card I am connecting them with, so no. Only options are to create a raid array.

---

