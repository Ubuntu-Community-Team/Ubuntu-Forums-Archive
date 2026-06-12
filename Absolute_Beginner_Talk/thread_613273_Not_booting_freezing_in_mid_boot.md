---
title: "Not booting freezing in mid boot"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by vincedia on 2007-11-14
I have Dapper installed on a dual partition PC. It was working fine till about a month ago when it just stoped loading. I've run it in recovery mode and it keeps freezing on 28.670225 drivers/usb/input/hid-core.c: v2.6:usb hid core driver

then it gives me an error after a good 15 mins;
ALERT! /dev/sdb3 does not exist. Dropping to a shell!

Does anyone know what device that could be? I have a USB keyboard and mouse and a USB hub with my printer attached. The keyboard is the Logitech G15 and the mouse is the MX revolution. Nothing has changed since this problem except I added a multi card reader that is USB. I removed it to try to get this resolved.

Thanks all in advance.
Vince

---

### Post by Tyche on 2007-11-14
> **vincedia said:**
> I have Dapper installed on a dual partition PC. It was working fine till about a month ago when it just stoped loading. I've run it in recovery mode and it keeps freezing on 28.670225 drivers/usb/input/hid-core.c: v2.6:usb hid core driver

then it gives me an error after a good 15 mins;
ALERT! /dev/sdb3 does not exist. Dropping to a shell!

Does anyone know what device that could be? I have a USB keyboard and mouse and a USB hub with my printer attached. The keyboard is the Logitech G15 and the mouse is the MX revolution. Nothing has changed since this problem except I added a multi card reader that is USB. I removed it to try to get this resolved.

Thanks all in advance.
Vince

This doesn't sound like it's related to USB.  /dev/sd* is a SCSI disk designation.  A likely possibility is that the UUID of the drive is not recognized.  This can happen when there is a fresh install on a different partition, or when a partition is changed or formatted.  The first place I'd look is to compare the UUID numbers to those in the /etc/fstab file.

To do this, open 2 terminals.  In one, type "blkid" (without the quotes and hit enter.  In the other, type "sudo gedit /etc/fstab" (without the quotes) and hit enter.  In both cases, the drives/partitions will be listed both by their /dev/sd* and by their UUID.  Compare the two.  If one in the /etc/fstab does not match the one from blkid, then change the one in /etc/fstab to match.  Save and close /etc/fstab, and reboot.  This should solve the problem.

If the UUID numbers DO match between the blkid command and the /etc/fstab, then close /etc/fstab WITHOUT saving. and hope that someone else has a better idea.  In any case, I wish you the best.

---

### Post by vincedia on 2007-11-14
I can't get into the OS at all. It just freezes there.

The best I can get is the shell prompt. Is there a way I can check those from the shell?

Thanks,
V

---

