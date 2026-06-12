---
title: "Can't mount USB CD writer (ASUS QuieTrack)"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by Steff_DK on 2006-01-17
I can't mount my USB CD writer and write files to the CDs.

The CD drive shows up in both "Places->Computer" and "GnomeBaker".
When I try to mount it, I get: "mount: special device /dev/hde does not exist"

How do I solve this ? :confused:

---

### Post by Steff_DK on 2006-01-17
Obviously not the most 'exotic' topic :rolleyes:  but still hoping for a little help here:

I have now tried various versions of the mount command w/o any luck :(  
```
sudo mount /dev/cdrom /mnt/cdrom
```

Do I need to put a hde file or folder in the dev folder for it to work, and then write the command mount /dev/hde... ??

I have searched the forum, but still haven't found a solution ...

---

### Post by earobinson on 2006-01-17
when you plug it in post your dmesg.

also its probaly not cdrom since you probaly have a cdrom allready its probaly cdrom1 or something

---

### Post by Steff_DK on 2006-01-17
Part of the dmesg:
```
[4301739.615000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[4301739.830000] scsi1 : SCSI emulation for USB Mass Storage devices
[4301739.831000] usb-storage: device found at 4
[4301739.831000] usb-storage: waiting for device to settle before scanning
[4301744.834000]   Vendor: ASUS      Model: CRW-5232AS        Rev: 1.01
[4301744.834000]   Type:   CD-ROM                             ANSI SCSI revision : 00
[4301744.867000] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[4301744.867000] Uniform CD-ROM driver Revision: 3.20
[4301744.870000] Attached scsi CD-ROM sr0 at scsi1, channel 0, id 0, lun 0
[4301744.874000] usb-storage: device scan complete
[4301748.252000] Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  ty pe 0
[4301748.255000] Attached scsi generic sg1 at scsi1, channel 0, id 0, lun 0,  ty pe 5
[4301880.820000] cdrom: This disc doesn't have any tracks I recognize!
[4301880.855000] cdrom: This disc doesn't have any tracks I recognize!
[4301922.857000] cdrom: This disc doesn't have any tracks I recognize!
[4301922.892000] cdrom: This disc doesn't have any tracks I recognize!
[4317673.099000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4317673.099000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4317673.232000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4317673.232000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

```

You're right - it's there as cd-rom 1. (?)

---

