---
title: "sata = sda or hda ?"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by noodles12 on 2006-07-29
My sata harddrive partitions show up as sda1/sda2/sda3/sda4/sda5. Someone todl me that sda meant usb connected devices. Could this be probably why ubuntu won't recognize my ext3 partition with linux on it?

---

### Post by guru369 on 2006-07-29
> **noodles12 said:**
> My sata harddrive partitions show up as sda1/sda2/sda3/sda4/sda5. Someone todl me that sda meant usb connected devices. Could this be probably why ubuntu won't recognize my ext3 partition with linux on it?

sda = SATA
sdc = USB Storage


You can check this when you insert a USB Storage devide and type: dmesg

---

### Post by philippe_carlo on 2006-07-29
All the sd devices can be either usb or serial ata. 'SD' stands for serial device, I believe, and both USB disks and SATA disks are serial devices and end up using the same bus. Wether hda is serial or usb depends on the order in which the devices are connected.

---

### Post by diepruis on 2006-07-29
[QUOTE="philippe_carlo"]Wether hda is serial or usb depends on the order in which the devices are connected.[/QUOTE]

Shouldn't hda there be sda?

---

### Post by philippe_carlo on 2006-07-29
Of course, thanks.

Ph

---

### Post by diepruis on 2006-07-29
No problem, I love being a nitpicker :)

---

### Post by steve.horsley on 2006-07-29
My understanding is that sd stands for SCSI drive. SCSIdrives have always been sd?. Other drivers do SCSI emulation. The CDROM driver whenthrough a phase where it was emulating a SCSI drive, so for a while I had a hard drive that was hda and a CDROM that was sda. Nowadays I have the reverse - the CDROM is IDE and seen as hda, but the hard drive is SATA, emulated SCSI and is seen as sda. USB disks also emulate SCSI, so they appear as sd? too.

---

