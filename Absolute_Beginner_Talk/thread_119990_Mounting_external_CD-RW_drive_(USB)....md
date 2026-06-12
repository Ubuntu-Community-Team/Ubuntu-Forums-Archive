---
title: "Mounting external CD-RW drive (USB)..."
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by Steff_DK on 2006-01-20
Hi all,

I cannot mount my ASUS USB CD-RW drive.
It is present but unusable in *places->computer->CD-ROM 1*
It is also present but unusable in gnomebaker.

When I right click it and click *mount* I get the following error:
*mount: special device /dev/hde does not exist*
There is not anything *hde* in my *dev* folder ...

When I use the following command, the drive spins up, but isn't mounted :( 
```
sudo mount /dev/cdrom /mnt/cdrom
```

My dmesg after I plug it in looks like this:
```
[4318107.925000] usb 1-2: new full speed USB device using uhci_hcd and address 5[4318108.024000] scsi2 : SCSI emulation for USB Mass Storage devices
[4318108.028000] usb-storage: device found at 5
[4318108.028000] usb-storage: waiting for device to settle before scanning
[4318113.031000]   Vendor: ASUS      Model: CRW-5232AS        Rev: 1.01
[4318113.031000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[4318113.042000] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[4318113.045000] Attached scsi CD-ROM sr0 at scsi2, channel 0, id 0, lun 0
[4318113.048000] Attached scsi generic sg0 at scsi2, channel 0, id 0, lun 0,  type 5
[4318113.059000] usb-storage: device scan complete
```

Help please - I desperately need to make a CD [-o<

---

### Post by wrtrdood on 2006-01-20
Check /dev/cdrom with ls -l and see what it's a link to.  Chances are it's the wrong device.  At any rate, you should be able to mount the drive with the same command but substitute /dev/cdrom with /dev/sr0.  It's what I use and it works quite well.  Also, check the permissions on the drive device to be sure you have full access.  That can be a problem.

Good luck.

---

### Post by Steff_DK on 2006-01-21
Where can I see a list of available mount points?

can't mount on neither *mnt/cdrom* or *mnt/cdrom1* :-k 

Thanks!

---

### Post by ysse on 2006-01-21
And you're sure you didn't forget sudo before mount? If you post the error messages you get when you try to mount, it would be a little easier to reply.

But as for available mount points, any empty directory with proper permissions will do. But it must exist. 

$ ls -ld /media/cdrom0
drwxr-xr-x  2 root root 48 2005-12-25 23:27 /media/cdrom0

---

### Post by Steff_DK on 2006-01-21
[QUOTE=ysse]any empty directory with proper permissions will do. But it must exist.[/QUOTE]

The penny drops! :D 

I mounted it (read-only) with this command:
```
sudo mount /dev/sr0 /media/cdrom0
mount: block device /dev/sr0 is write-protected, mounting read-only
```

Doesn't the dev/sr0 support CD-writers? -so I can write CDs as well ...

---

### Post by wrtrdood on 2006-01-24
Hmmm... yes, it should.  Be sure the correct media is in the drive and check that /dev/sr0 has write permissions (ls -l /dev/sr0).  You could also look at /media/cdrom0 for contents of the CD if it properly mounted.

A good way to check properties of the device itself is to use *cdrecord -scanbus*.  It should show up in the list.  Also, take a look at your log files under /var/log.  That should give you some info about the drive as well.  I've used both of my externals as writers with no problem for both CD and DVD so, yes, it can be done.

---

