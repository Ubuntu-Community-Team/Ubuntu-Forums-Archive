---
title: "USB Sticks don't mount"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by The Joe on 2006-11-22
Its a bit hard to explain but I'll try, when I put in my USB Disc (Novatech if it helps), it doesn't appear on the Desktop, in Places or anywhere. Its just not getting read. However when I use my completely formatted MP3 Player I can use it as a normal USB Disc. Any ideas?

And no. I did not join these forums just to post this one thing.

---

### Post by ajgreeny on 2006-11-22
Have you looked in /media/sda to see if it is mounted there, but just not showing on the desktop.  On my machine using kubuntu 6.06, usb sticks are always mounted /media/sdX, where the X sometimes is a, b, c, d, or even once, e.  I never worked out why the change of final letter, but it was always mounted so didn't care too much,  That was on breezy; now on dapper it is always, I think, sda.

---

### Post by procras on 2006-11-22
look at syslog while you plug in the stick

$ tail -f /var/log/syslog
Nov 22 21:50:18 billy -- MARK --
Nov 22 22:07:39 billy kernel: [17353550.916000] usb 4-2: new full speed USB device using uhci_hcd and address 2
Nov 22 22:07:39 billy kernel: [17353551.096000] usb 4-2: configuration #1 chosen from 1 choice
Nov 22 22:07:40 billy kernel: [17353551.640000] usbcore: registered new driver libusual
Nov 22 22:07:40 billy kernel: [17353551.688000] Initializing USB Mass Storage driver...
Nov 22 22:07:40 billy kernel: [17353551.688000] scsi2 : SCSI emulation for USB Mass Storage devices
Nov 22 22:07:40 billy kernel: [17353551.688000] usb-storage: device found at 2
Nov 22 22:07:40 billy kernel: [17353551.688000] usb-storage: waiting for device to settle before scanning
Nov 22 22:07:40 billy kernel: [17353551.688000] usbcore: registered new driver usb-storage
Nov 22 22:07:40 billy kernel: [17353551.688000] USB Mass Storage support registered.
Nov 22 22:07:45 billy kernel: [17353556.688000] usb-storage: device scan complete
Nov 22 22:07:45 billy kernel: [17353556.692000]   Vendor: CRUCIAL   Model: USB DRIVE         Rev: 1.12
Nov 22 22:07:45 billy kernel: [17353556.692000]   Type:   Direct-Access                      ANSI SCSI revision: 01 CCS
Nov 22 22:07:45 billy kernel: [17353556.696000] SCSI device sdc: 503808 512-byte hdwr sectors (258 MB)
Nov 22 22:07:45 billy kernel: [17353556.700000] sdc: Write Protect is off
Nov 22 22:07:45 billy kernel: [17353556.700000] sdc: Mode Sense: 23 00 00 00
Nov 22 22:07:45 billy kernel: [17353556.700000] sdc: assuming drive cache: write through
Nov 22 22:07:45 billy kernel: [17353556.712000] SCSI device sdc: 503808 512-byte hdwr sectors (258 MB)
Nov 22 22:07:45 billy kernel: [17353556.716000] sdc: Write Protect is off
Nov 22 22:07:45 billy kernel: [17353556.716000] sdc: Mode Sense: 23 00 00 00
Nov 22 22:07:45 billy kernel: [17353556.716000] sdc: assuming drive cache: write through
Nov 22 22:07:45 billy kernel: [17353556.716000]  sdc: sdc1
Nov 22 22:07:45 billy kernel: [17353556.724000] sd 2:0:0:0: Attached scsi removable disk sdc
Nov 22 22:07:45 billy kernel: [17353556.724000] sd 2:0:0:0: Attached scsi generic sg2 type 0
Nov 22 22:07:46 billy kernel: [17353557.824000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

How does this compare with what happens when you use the mp3 thingy that works.

See if the stick is recognised. The sdc thing above tells you where your box will look for the stick. If the stick is recognised and it does not appear on your desktop you can try and mount it manually or check that you  have not unset the mount optiosn for removable drives and media in 
System->Prefernces->Removable Drives and Media->Storage

Also if the stick is not recognised at all
- Try a different USB port, Bad connection.
- Have you too many things plugged into the USB system? Does the stick work when you pull out the scanner, printer, mouse, keyboard or whatever.
- Try the stick on another box to see if there is a problem there too, the stick may be kaput

---

### Post by procras on 2006-11-23
See also this thread 
[http://www.ubuntuforums.org/showthread.php?t=304623]("http://www.ubuntuforums.org/showthread.php?t=304623")

---

### Post by The Joe on 2006-11-23
Ok I'll take a look at my syslog later. I can't at the moment I'm still waiting for a router to get the internet on my Ubuntu install.

---

### Post by taurus on 2006-11-23
Applications -> Accessories -> Terminal

```
sudo mkdir /media/usb
sudo mount -t vfat /dev/sdc1 /media/usb
```

---

### Post by sailor2001 on 2006-11-23
also your box may have usb 1 and usb 2 ports  (aged)   change ports and see if that'll do it

---

### Post by The Joe on 2006-11-24
I got it working but its a big inconvenience for me because the only working port is at the back of the computer. The front two won't mount it.

---

### Post by taurus on 2006-11-24
Have you checked the cable from the mobo to the front ports of your case?

---

### Post by The Joe on 2006-11-24
Its not really the easiest thing in the world for me to crack open my tower.

---

