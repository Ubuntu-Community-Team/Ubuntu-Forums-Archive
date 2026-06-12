---
title: "FireWire drive not recognized by sysfs after suspend/resume"
date: 2009-03-04
forum: Apple Hardware Users
---

### Post by coiske on 2009-03-04
My external FireWire drive is recognized and automounted by sysfs/udev/hal the first time I plug it in and turn it on.  If I unmount it, turn it off, and turn it back on, it is recognized and automounted again.  So far so good.

But if I unmount and turn off the FireWire drive, suspend my computer, and later resume, there doesn't seem to be any way to remount the FireWire drive.

As best I can tell, here's what seems to be happening.  When the drive is initially automounted, sysfs recognizes it (as shown by the sudden appearance of /sys/block/sda).  Sysfs then creates /dev/sda (and /dev/sda1).  Udev notices a new device on the tree, and passes it along to hal, which mounts it (and puts a correspondng entry in /media/.hal-mtab).  When I unmount the drive, hal removes the mount (and its .hal-mtab entry).  /dev/sda, /dev/sda1, and /sys/block/sda persist until the drive is powered off or disconnected.  Until then, "pmount /dev/sda1" can be used to remount the drive.  Powering the drive back on recreates /sys/block/sda, /dev/sda, /dev/sda1, and the entry in /media/.hal-mtab (and yields a successful re-automount).

But when I unmount and turn off the firewire drive, suspend the computer, resume, and then power the drive on, /sys/block/sda never gets created.  Since sysfs doesn't even recognize the drive this time around, udev and hal never get a chance to automount it.  (And I can't figure out how to manually mount a device that hasn't been recognized by sysfs.)

I'm at a loss how to troubleshoot (or work around) this problem.  Any thoughts would be greatly appreciated.

David

PS I'm running Intrepid on a PowerBook G4.

---

### Post by cyberdork33 on 2009-03-04
after you resume, does restarting hal help? (sudo /etc/init.d/hal restart)

---

### Post by coiske on 2009-03-04
Thanks for the suggestion!  Unfortunately, restarting hal didn't help.  Nor did restarting udev.  /sys/block/sda still doesn't appear, suggesting that sysfs isn't seeing the drive.  And until sysfs sees it, udev and hal never get a chance to take a crack at it.  So if there were only some way to restart sysfs, maybe that would help....

---

### Post by cyberdork33 on 2009-03-04
> **coiske said:**
> Thanks for the suggestion!  Unfortunately, restarting hal didn't help.  Nor did restarting udev.  /sys/block/sda still doesn't appear, suggesting that sysfs isn't seeing the drive.  And until sysfs sees it, udev and hal never get a chance to take a crack at it.  So if there were only some way to restart sysfs, maybe that would help....
It could also be firewire in general... maybe you could try unloading /reloading the ieee1394 stuff...

---

### Post by coiske on 2009-03-04
Good call!  Doing the following after resuming solved the problem:

su
modprobe -r sbp2 dv1394 raw1394 ieee1394
modprobe ieee1394
modprobe raw1394
modprobe dv1394
modprobe sbp2

I tried putting a script to do this in /etc/acpi/resume.d/ , but that caused havoc if I accidentally left the FireWire drive mounted before suspending/resuming.  So I'll just manually run my script if I want to mount my FireWire drive after resuming.

Thanks for your help!!!

---

