---
title: "Problem with a digital camera"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by mgmariom on 2006-08-01
Hi,
i'm trying to use my Sony dsc t5 but i dont get it work

When i connect it to the usb port, the "GNOME Device Manager" recognize it, but the camora is not mounted.

i've tried to find the associated /dev/xxx to this usb device.
Unfortunately, i found no info about the corresponding /dev anyhere. i only found /dev/sda1-6 (used by the hard drive), and /dev/scd0 (cdrom)

how can i discover, which /dev/xxx corresponds to this usb device??
and, in the case that there is no /dev/ already created, how can i find the major/minor needed to invoke mknod??

thanks in advance,
Mario

---

### Post by patrick295767 on 2006-08-01
> **mgmariom said:**
> Hi,
i'm trying to use my Sony dsc t5 but i dont get it work

When i connect it to the usb port, the "GNOME Device Manager" recognize it, but the camora is not mounted.

i've tried to find the associated /dev/xxx to this usb device.
Unfortunately, i found no info about the corresponding /dev anyhere. i only found /dev/sda1-6 (used by the hard drive), and /dev/scd0 (cdrom)

how can i discover, which /dev/xxx corresponds to this usb device??
and, in the case that there is no /dev/ already created, how can i find the major/minor needed to invoke mknod??

thanks in advance,
Mario

plug unplug 
and type dmesg.

---

### Post by hw-tph on 2006-08-01
First off, watch the logs when connecting the camera. It will probable reveal some tidbit of useful information. Try **tail -f /var/log/syslog** in a terminal window and then plug in the camera. Since you already have a SCSI (or S-ATA disk using libata) that grabs the first available SCSI disk name, sda. It is possible that the camera is detected as sdb or by other names, but it should be readable in the log output. Also check the output (last few lines) of the **dmesg** command.


Håkan

---

