---
title: "totally screwed up!"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-03-03
i don't think i ever set things up to mount my camera properly, but i had it working somehow. i must have messed with it too often and now i'm getting "mount: special device /dev/sda1 does not exist" when i enter "sudo mount /dev/sda1 ~/camera -t vfat". am i screwed here?

---

### Post by LordBug on 2006-03-03
Ubuntu is pretty good about auto-mounting things.  If you plug your camera in, do you get a new icon on the desktop?

If not, check out dmesg(?) to see what device the camera is.  It might not be SDA1 now.

---

### Post by fuscia on 2006-03-03
[QUOTE=LordBug]Ubuntu is pretty good about auto-mounting things.  If you plug your camera in, do you get a new icon on the desktop?

If not, check out dmesg(?) to see what device the camera is.  It might not be SDA1 now.[/QUOTE]

i'm using openbox which doesn't automount my camera. 

just did this...


 dmesg | tail
[4526296.619000] sdb: Write Protect is off
[4526296.619000] sdb: Mode Sense: 18 00 00 08
[4526296.619000] sdb: assuming drive cache: write through
[4526296.634000] SCSI device sdb: 990976 512-byte hdwr sectors (507 MB)
[4526296.636000] sdb: Write Protect is off
[4526296.636000] sdb: Mode Sense: 18 00 00 08
[4526296.636000] sdb: assuming drive cache: write through
[4526296.636000]  /dev/scsi/host18/bus0/target0/lun0: p1
[4526296.650000] Attached scsi removable disk sdb at scsi18, channel 0, id 0, lun 0
[4526296.656000] usb-storage: device scan complete

that's all martian to me, unfortunately.

somehow, /dev/sda1 appears to no longer exist and that's where i think the trouble is.

---

### Post by fuscia on 2006-03-03
i can get to my camera using nautilus, by clicking on the 'computer' icon. i can mount it there and get to my pics. the problem is that i don't want to be stuck using nautilus. i just can't find any other file manager that has that 'computer' option.

---

### Post by Q4U on 2006-03-03
So /dev/sda1 does not appear in your etc/fstab? Please check it. Q4U

PS I had a problem with my camera, it turned out to be a permission error in mounting the partition. Had to replace "defaults" after the filesystem type with "iocharset=utf8,umask=0000" and remount with sudo mount -a.

---

### Post by Pragmatist on 2006-03-03
type this with your camera unplugged: ```
tail -f /var/log/messages
```

Then plugin your camera and watch for new text on your terminal.  It should tell you where the mount point is.
If you want to guarantee the mount point is the same very every time, I believe you make a rule in /etc/udev

---

### Post by towsonu2003 on 2006-03-03
did you chack what /dev/sdb1 is? also, some cameras (example: Canon G6, works with gtkam) don't get mounted at all, but I guess yours isn't one.

---

### Post by fuscia on 2006-03-03
[QUOTE=Pragmatist]type this with your camera unplugged: ```
tail -f /var/log/messages
```

Then plugin your camera and watch for new text on your terminal.  It should tell you where the mount point is.
If you want to guarantee the mount point is the same very every time, I believe you make a rule in /etc/udev[/QUOTE]

ok, i did that and this is what i ended up with...

"Mar  3 17:32:24 localhost kernel: [4533140.721000] usb 1-2.2: new full speed USB device using uhci_hcd and address 29
Mar  3 17:32:24 localhost kernel: [4533140.800000] scsi22 : SCSI emulation for USB Mass Storage devices
Mar  3 17:32:24 localhost usb.agent[27578]:      usb-storage: already loaded
Mar  3 17:32:29 localhost kernel: [4533145.807000]   Vendor: NIKON     Model: NIKON DSC E5600   Rev: 1.00
Mar  3 17:32:29 localhost kernel: [4533145.807000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Mar  3 17:32:29 localhost kernel: [4533145.819000] SCSI device sdb: 990976 512-byte hdwr sectors (507 MB)
Mar  3 17:32:29 localhost kernel: [4533145.822000] sdb: Write Protect is off
Mar  3 17:32:29 localhost kernel: [4533145.836000] SCSI device sdb: 990976 512-byte hdwr sectors (507 MB)
Mar  3 17:32:29 localhost kernel: [4533145.838000] sdb: Write Protect is off
Mar  3 17:32:29 localhost kernel: [4533145.838000]  /dev/scsi/host22/bus0/target0/lun0: p1
Mar  3 17:32:29 localhost kernel: [4533145.853000] Attached scsi removable disk sdb at scsi22, channel 0, id 0, lun 0
Mar  3 17:32:29 localhost scsi.agent[27625]:      sd_mod: loaded sucessfully (for disk)"

unfortunately, i don't understand any of that. (pretend you're helping your grandmother.)

---

### Post by Pragmatist on 2006-03-03
> SCSI device sdb  I don't understand all of it either.  But your camera is probably at /dev/sdbX where X is some number, probably 1.  I would try mounting it as you did in the past, but try /dev/sdb1 instead of /dev/sda1

Let us know what happens.

---

### Post by fuscia on 2006-03-03
[QUOTE=Pragmatist]I don't understand all of it either.  But your camera is probably at /dev/sdbX where X is some number, probably 1.  I would try mounting it as you did in the past, but try /dev/sdb1 instead of /dev/sda1

Let us know what happens.[/QUOTE]

holy cow! that worked! thank you much. i just had to alter the entry in /etc/fstab to /dev/sdb1 instead of /dev/sda1 and the rest worked out. the one thing that concerns me though is the idea that it doesn't always mount in the same place. i guess now that i know that, and with the process you showed me for finding where it does mount, and knowing that it does indeed mount somewhere, it will be easier to find if i get lost again. thanks.

---

### Post by Pragmatist on 2006-03-03
Great!  Well, now that you know what to do if this happens again you don't have to worry.  If you want to *prevent* it from happening again, check out these tutorials:

[http://www.togaware.com/linux/survivor/Using_UDEV.shtml](http://www.togaware.com/linux/survivor/Using_UDEV.shtml)
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)
and typing **man udev** gives you the manpage for **udev** which is also informative.

The main idea is that **udev** was created to specifically avoid the problem you are experiencing.  Before the 2.6 kernel this was an annoying problem.  However, now if you want persistent naming of devices, you write a small rule so that **udev** "knows" that you always want a specific device attached to a specific mount point.

---

### Post by fuscia on 2006-03-03
thanks, pragmatist. and thanks to all who responded to this thread.

---

