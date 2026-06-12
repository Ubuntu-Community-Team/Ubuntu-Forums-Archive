---
title: "Ubunto freezing on load-up"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Prodromoi on 2008-01-18
A previously working installation of Ubunto 7.10 (i386) has stopped working.  Now, when the first "loading bar" appears it halts about 20% of the way along, pauses for around three/four minutes then the loading bar carries on the the end.  The monitor then displays the last screen of the log; I don't know how to scroll back up to view more - the only error I can see on this screen is:

Starting powernowd...
/etc/rc2.d/S20powernowd: 156: cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling_governer: Directory nonexistent

Restarting the computer at this point ends up with (eventually) the same message consistently.
I had not changed the clock speed for ages.  Checking in the BIOS, the clock speed was as it should be.  I've even tried underclocking the CPU to see if it makes any difference - it doesn't.

Booting from a Live CD works just fine.


I suspect that whatever has gone wrong is a result of what I was working on immediately before the error occurred, which was trying to get the webcam working on my partner's computer.

Having plugged it in (a USB Logitech Sphere) I downloaded and ran Easycam - which didn't find a driver.  I removed Easycam and installed Easycam 2.  This seemed to find and install a driver, although the webcam still wasn't working.  (The error was something like "cannot find /dev/webcam0" or similar.)

When I downloaded & installed Easycam (via SPM) it required a handful of other packages and libraries - but unfortunately I didn't pay a great deal of attention to them and don't know what they were.

So... forget the webcam... how can I get this machine booting up again?

---

### Post by Cypher on 2008-01-18
When at the GRUB menu, highlight the first Ubuntu entry (usually the default) and hit the 'E' key to edit the entry. Here you should see the command line options, at the end you will "ro quiet splash" as options. Remove the "quiet splash" words and then boot into Ubuntu.

This will get rid of the loading progress bar and also make the Kernel spit out what it's doing during the loading process. This might help us better pinpoint the culprit.

Once we find the offending script/program, we can use the "recovery mode" to get into Ubuntu and remove that particular script/program..

---

### Post by philinux on 2008-01-18
Click the link below for known bugs.

You could also try installing and running startupmanager.

---

### Post by Prodromoi on 2008-01-18
OK, this is odd.  Maybe obvious.. but still odd.

I've unplugged the webcam and the system now boots up as it used to do.  So is there any file output that I can get that will help shed light?

---

### Post by philinux on 2008-01-18
/var/log/messages.log I think. Not on buntu box just now.

---

### Post by Prodromoi on 2008-01-18
I am trying to paste the content of /var/log/messages as a reply here in the code tags but I think it is too long, since the browser keeps going blank on me.  Working on it...

---

### Post by Prodromoi on 2008-01-18
OK, the file content is here:
[http://altreacher.f2s.com/temp/messages](http://altreacher.f2s.com/temp/messages)

---

### Post by philinux on 2008-01-18
How many usb hubs have you got? Have you tried plugging webcam into main usb port rather than a hub?

---

### Post by Prodromoi on 2008-01-18
The motherboard has a USB 1.1 hub.  In addtion to that the machine has a PCI USB2 card which gives it four rear USB2 ports, into which the mouse etc are plugged.  The only thing using the USB 1.1 hub is the internal card reader (because only the motherboard has the necessary internal-type of USB connector.)

I tried the webcam in one of the USB2 ports that the PCI card provide.  I haven't tried it in any of the motherboard USB1.1 ports since I doubt they would be fast enough.

---

### Post by philinux on 2008-01-18
See what this shows up. Copy and paste it into the terminal.

dmesg | grep -i usb

Not sure if sudo needed. On a vista(yughh) laptop.

---

### Post by Prodromoi on 2008-01-18
OK, done.  I have no clue what it means...!
```
~$ dmesg | grep -i usb
[   28.273974] usbcore: registered new interface driver usbfs
[   28.274012] usbcore: registered new interface driver hub
[   28.274040] usbcore: registered new device driver usb
[   28.275024] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   28.275575] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[   28.352884] usb usb1: configuration #1 chosen from 1 choice
[   28.352927] hub 1-0:1.0: USB hub found
[   28.433887] USB Universal Host Controller Interface driver v3.0
[   28.455644] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
[   28.513314] usb usb2: configuration #1 chosen from 1 choice
[   28.513358] hub 2-0:1.0: USB hub found
[   28.615592] ohci_hcd 0000:00:09.0: new USB bus registered, assigned bus number 3
[   28.673247] usb usb3: configuration #1 chosen from 1 choice
[   28.673287] hub 3-0:1.0: USB hub found
[   28.775505] ohci_hcd 0000:00:09.1: new USB bus registered, assigned bus number 4
[   28.833131] usb usb4: configuration #1 chosen from 1 choice
[   28.833165] hub 4-0:1.0: USB hub found
[   28.919012] usb 2-3: new full speed USB device using ohci_hcd and address 2
[   28.935233] ohci_hcd 0000:00:09.2: new USB bus registered, assigned bus number 5
[   28.993117] usb usb5: configuration #1 chosen from 1 choice
[   28.993162] hub 5-0:1.0: USB hub found
[   29.195954] usb 2-3: configuration #1 chosen from 1 choice
[   29.502796] usb 4-2: new low speed USB device using ohci_hcd and address 2
[   29.750924] usb 4-2: configuration #1 chosen from 1 choice
[   29.755926] usbcore: registered new interface driver libusual
[   29.767893] Initializing USB Mass Storage driver...
[   29.768010] scsi2 : SCSI emulation for USB Mass Storage devices
[   29.768076] usb-storage: device found at 2
[   29.768078] usb-storage: waiting for device to settle before scanning
[   29.768097] usbcore: registered new interface driver usb-storage
[   29.768101] USB Mass Storage support registered.
[   29.788373] ehci_hcd 0000:00:09.3: new USB bus registered, assigned bus number 6
[   29.795927] usbcore: registered new interface driver hiddev
[   29.810820] ehci_hcd 0000:00:09.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.810902] usb 4-2: USB disconnect, address 2
[   29.811085] usb usb6: configuration #1 chosen from 1 choice
[   29.811121] hub 6-0:1.0: USB hub found
[   29.818282] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:09.1-2
[   29.915009] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 7
[   29.915077] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   29.915170] usb usb7: configuration #1 chosen from 1 choice
[   29.915201] hub 7-0:1.0: USB hub found
[   30.019132] uhci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 8
[   30.019308] usb usb8: configuration #1 chosen from 1 choice
[   30.019350] hub 8-0:1.0: USB hub found
[   30.122812] uhci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 9
[   30.122996] usb usb9: configuration #1 chosen from 1 choice
[   30.123028] hub 9-0:1.0: USB hub found
[   30.126657] usbcore: registered new interface driver usbhid
[   30.126665] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   30.430453] usb 4-2: new low speed USB device using ohci_hcd and address 3
[   30.678646] usb 4-2: configuration #1 chosen from 1 choice
[   30.699853] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:09.1-2
[   34.771010] usb-storage: device scan complete
```

---

