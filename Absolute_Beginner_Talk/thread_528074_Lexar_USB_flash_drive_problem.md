---
title: "Lexar USB flash drive problem"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by justin_blair on 2007-08-17
Hi, I have a 4gb Lexar Firefly flash drive with a FAT32 file system.  I have 4 USB ports and the drive now only works in two of them, problem is it's the two on the back of the computer that work.  Two days ago or so, it worked in all of them.  Can someone please help me get it to work in the front two usb ports?

---

### Post by Pragmatist on 2007-08-17
Are all the USB ports the same (i.e. are they both USB 2.0) ?

---

### Post by justin_blair on 2007-08-17
Yes both USB 2.0.  I checked the connections and they appear to be connected well to the motherboard.

---

### Post by Pragmatist on 2007-08-17
Try this:

With the device unplugged, type this in a terminal,
```
tail -f /var/log/messages
```

Now plug the device in to one of the ports that do NOT work, then unplug it and plug it into another one that does NOT work, and post the output of all of that here.

Then start over:
unplug the device, type CTRL-C to end the tail command, run the tail command again:
```
tail -f /var/log/messages
```
Now plug the device into one of the working USB ports, then plug it into the other, then post the output here.

We will compare the results.

---

### Post by justin_blair on 2007-08-17
Ok here is the not working ports:

> justin@Vinyasa:~$ tail -f /var/log/messages
Aug 17 09:25:35 Vinyasa kernel: [ 4604.773292] usb 5-7: new high speed USB device using ehci_hcd and address 118
Aug 17 09:25:35 Vinyasa kernel: [ 4604.906980] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 09:25:35 Vinyasa kernel: [ 4604.907229] scsi1590 : SCSI emulation for USB Mass Storage devices
Aug 17 09:25:36 Vinyasa kernel: [ 4605.036708] usb 5-7: USB disconnect, address 118
Aug 17 09:25:36 Vinyasa kernel: [ 4605.276107] usb 5-7: new high speed USB device using ehci_hcd and address 119
Aug 17 09:25:36 Vinyasa kernel: [ 4605.906623] usb 5-7: new high speed USB device using ehci_hcd and address 120
Aug 17 09:25:37 Vinyasa kernel: [ 4606.537135] usb 5-7: new high speed USB device using ehci_hcd and address 121
Aug 17 09:25:37 Vinyasa kernel: [ 4606.892301] usb 5-7: new high speed USB device using ehci_hcd and address 122
Aug 17 09:49:07 Vinyasa -- MARK --
Aug 17 10:09:07 Vinyasa -- MARK --
Aug 17 10:14:02 Vinyasa kernel: [ 7505.205222] usb 5-7: new high speed USB device using ehci_hcd and address 123
Aug 17 10:14:02 Vinyasa kernel: [ 7505.338793] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:02 Vinyasa kernel: [ 7505.339172] scsi1591 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:03 Vinyasa kernel: [ 7505.720034] usb 5-7: USB disconnect, address 123
Aug 17 10:14:03 Vinyasa kernel: [ 7505.959452] usb 5-7: new high speed USB device using ehci_hcd and address 124
Aug 17 10:14:03 Vinyasa kernel: [ 7506.093264] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:03 Vinyasa kernel: [ 7506.093513] scsi1592 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:04 Vinyasa kernel: [ 7506.474254] usb 5-7: USB disconnect, address 124
Aug 17 10:14:04 Vinyasa kernel: [ 7506.713668] usb 5-7: new high speed USB device using ehci_hcd and address 125
Aug 17 10:14:04 Vinyasa kernel: [ 7506.847516] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:04 Vinyasa kernel: [ 7506.847759] scsi1593 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:05 Vinyasa kernel: [ 7507.731376] usb 5-7: USB disconnect, address 125
Aug 17 10:14:05 Vinyasa kernel: [ 7507.970716] usb 5-7: new high speed USB device using ehci_hcd and address 126
Aug 17 10:14:05 Vinyasa kernel: [ 7508.106454] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:05 Vinyasa kernel: [ 7508.106688] scsi1594 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:05 Vinyasa kernel: [ 7508.234120] usb 5-7: USB disconnect, address 126
Aug 17 10:14:06 Vinyasa kernel: [ 7508.473523] usb 5-7: new high speed USB device using ehci_hcd and address 127
Aug 17 10:14:06 Vinyasa kernel: [ 7508.607258] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:06 Vinyasa kernel: [ 7508.607500] scsi1595 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:06 Vinyasa kernel: [ 7508.736927] usb 5-7: USB disconnect, address 127
Aug 17 10:14:06 Vinyasa kernel: [ 7508.976337] usb 5-7: new high speed USB device using ehci_hcd and address 2
Aug 17 10:14:06 Vinyasa kernel: [ 7509.110077] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:06 Vinyasa kernel: [ 7509.110342] scsi1596 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:07 Vinyasa kernel: [ 7509.742555] usb 5-7: USB disconnect, address 2
Aug 17 10:14:07 Vinyasa kernel: [ 7509.981970] usb 5-7: new high speed USB device using ehci_hcd and address 3
Aug 17 10:14:07 Vinyasa kernel: [ 7510.115724] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:07 Vinyasa kernel: [ 7510.115975] scsi1597 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:08 Vinyasa kernel: [ 7510.748186] usb 5-7: USB disconnect, address 3
Aug 17 10:14:08 Vinyasa kernel: [ 7510.987600] usb 5-7: new high speed USB device using ehci_hcd and address 4
Aug 17 10:14:09 Vinyasa kernel: [ 7511.969287] usb 5-7: new high speed USB device using ehci_hcd and address 5
Aug 17 10:14:09 Vinyasa kernel: [ 7512.103111] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:09 Vinyasa kernel: [ 7512.103374] scsi1598 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:10 Vinyasa kernel: [ 7512.759447] usb 5-7: USB disconnect, address 5
Aug 17 10:14:10 Vinyasa kernel: [ 7512.998862] usb 5-7: new high speed USB device using ehci_hcd and address 6
Aug 17 10:14:10 Vinyasa kernel: [ 7513.132551] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:10 Vinyasa kernel: [ 7513.132791] scsi1599 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:11 Vinyasa kernel: [ 7514.016490] usb 5-7: USB disconnect, address 6
Aug 17 10:14:11 Vinyasa kernel: [ 7514.255903] usb 5-7: new high speed USB device using ehci_hcd and address 7
Aug 17 10:14:12 Vinyasa kernel: [ 7514.886416] usb 5-7: new high speed USB device using ehci_hcd and address 8
Aug 17 10:14:12 Vinyasa kernel: [ 7515.020126] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:12 Vinyasa kernel: [ 7515.020369] scsi1600 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:13 Vinyasa kernel: [ 7516.027752] usb 5-7: USB disconnect, address 8
Aug 17 10:14:13 Vinyasa kernel: [ 7516.267165] usb 5-7: new high speed USB device using ehci_hcd and address 9
Aug 17 10:14:14 Vinyasa kernel: [ 7516.897679] usb 5-7: new high speed USB device using ehci_hcd and address 10
Aug 17 10:14:14 Vinyasa kernel: [ 7517.031412] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:14 Vinyasa kernel: [ 7517.031659] scsi1601 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:15 Vinyasa kernel: [ 7518.039014] usb 5-7: USB disconnect, address 10
Aug 17 10:14:15 Vinyasa kernel: [ 7518.278435] usb 5-7: new high speed USB device using ehci_hcd and address 11
Aug 17 10:14:16 Vinyasa kernel: [ 7518.412177] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:16 Vinyasa kernel: [ 7518.412427] scsi1602 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:16 Vinyasa kernel: [ 7518.793239] usb 5-7: USB disconnect, address 11
Aug 17 10:14:16 Vinyasa kernel: [ 7519.032650] usb 5-7: new high speed USB device using ehci_hcd and address 12
Aug 17 10:14:16 Vinyasa kernel: [ 7519.166427] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:16 Vinyasa kernel: [ 7519.166671] scsi1603 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:16 Vinyasa kernel: [ 7519.296062] usb 5-7: USB disconnect, address 12
Aug 17 10:14:17 Vinyasa kernel: [ 7519.535469] usb 5-7: new high speed USB device using ehci_hcd and address 13
Aug 17 10:14:17 Vinyasa kernel: [ 7519.669120] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:17 Vinyasa kernel: [ 7519.669357] scsi1604 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:17 Vinyasa kernel: [ 7520.050279] usb 5-7: USB disconnect, address 13
Aug 17 10:14:17 Vinyasa kernel: [ 7520.289691] usb 5-7: new high speed USB device using ehci_hcd and address 14
Aug 17 10:14:18 Vinyasa kernel: [ 7520.423352] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:18 Vinyasa kernel: [ 7520.423604] scsi1605 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:18 Vinyasa kernel: [ 7520.553097] usb 5-7: USB disconnect, address 14
Aug 17 10:14:18 Vinyasa kernel: [ 7520.792507] usb 5-7: new high speed USB device using ehci_hcd and address 15
Aug 17 10:14:19 Vinyasa kernel: [ 7521.774195] usb 5-7: new high speed USB device using ehci_hcd and address 16
Aug 17 10:14:19 Vinyasa kernel: [ 7521.907879] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:19 Vinyasa kernel: [ 7521.908265] scsi1606 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:19 Vinyasa kernel: [ 7522.061545] usb 5-7: USB disconnect, address 16
Aug 17 10:14:19 Vinyasa kernel: [ 7522.300952] usb 5-7: new high speed USB device using ehci_hcd and address 17
Aug 17 10:14:20 Vinyasa kernel: [ 7522.434648] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:20 Vinyasa kernel: [ 7522.434899] scsi1607 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:20 Vinyasa kernel: [ 7522.815765] usb 5-7: USB disconnect, address 17
Aug 17 10:14:20 Vinyasa kernel: [ 7523.055185] usb 5-7: new high speed USB device using ehci_hcd and address 18
Aug 17 10:14:20 Vinyasa kernel: [ 7523.188880] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:20 Vinyasa kernel: [ 7523.189124] scsi1608 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:21 Vinyasa kernel: [ 7524.072802] usb 5-7: USB disconnect, address 18
Aug 17 10:14:21 Vinyasa kernel: [ 7524.312218] usb 5-7: new high speed USB device using ehci_hcd and address 19
Aug 17 10:14:22 Vinyasa kernel: [ 7524.445940] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:22 Vinyasa kernel: [ 7524.446188] scsi1609 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:22 Vinyasa kernel: [ 7525.078434] usb 5-7: USB disconnect, address 19
Aug 17 10:14:22 Vinyasa kernel: [ 7525.317846] usb 5-7: new high speed USB device using ehci_hcd and address 20
Aug 17 10:14:23 Vinyasa kernel: [ 7525.451584] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:23 Vinyasa kernel: [ 7525.451830] scsi1610 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:23 Vinyasa kernel: [ 7525.581260] usb 5-7: USB disconnect, address 20
Aug 17 10:14:23 Vinyasa kernel: [ 7525.820661] usb 5-7: new high speed USB device using ehci_hcd and address 21
Aug 17 10:14:23 Vinyasa kernel: [ 7525.954410] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:23 Vinyasa kernel: [ 7525.954646] scsi1611 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:23 Vinyasa kernel: [ 7526.084075] usb 5-7: USB disconnect, address 21
Aug 17 10:14:23 Vinyasa kernel: [ 7526.323476] usb 5-7: new high speed USB device using ehci_hcd and address 22
Aug 17 10:14:24 Vinyasa kernel: [ 7526.457230] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:24 Vinyasa kernel: [ 7526.457469] scsi1612 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:24 Vinyasa kernel: [ 7526.586897] usb 5-7: USB disconnect, address 22
Aug 17 10:14:24 Vinyasa kernel: [ 7526.826292] usb 5-7: new high speed USB device using ehci_hcd and address 23
Aug 17 10:14:25 Vinyasa kernel: [ 7527.456806] usb 5-7: new high speed USB device using ehci_hcd and address 24
Aug 17 10:14:25 Vinyasa kernel: [ 7527.590453] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:25 Vinyasa kernel: [ 7527.590706] scsi1613 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:25 Vinyasa kernel: [ 7528.095326] usb 5-7: USB disconnect, address 24
Aug 17 10:14:26 Vinyasa kernel: [ 7528.334739] usb 5-7: new high speed USB device using ehci_hcd and address 25
Aug 17 10:14:26 Vinyasa kernel: [ 7528.468407] usb 5-7: configuration #1 chosen from 1 choice
Aug 17 10:14:26 Vinyasa kernel: [ 7528.468654] scsi1614 : SCSI emulation for USB Mass Storage devices
Aug 17 10:14:26 Vinyasa kernel: [ 7528.598152] usb 5-7: USB disconnect, address 25
Aug 17 10:14:29 Vinyasa kernel: [ 7531.914307] usb 5-8: new high speed USB device using ehci_hcd and address 26
Aug 17 10:14:30 Vinyasa kernel: [ 7532.919938] usb 5-8: new high speed USB device using ehci_hcd and address 27
Aug 17 10:14:31 Vinyasa kernel: [ 7533.913602] usb 5-8: new high speed USB device using ehci_hcd and address 28
Aug 17 10:14:32 Vinyasa kernel: [ 7534.544116] usb 5-8: new high speed USB device using ehci_hcd and address 29
Aug 17 10:14:33 Vinyasa kernel: [ 7535.426035] usb 5-8: new high speed USB device using ehci_hcd and address 31
Aug 17 10:14:33 Vinyasa kernel: [ 7535.928851] usb 5-8: new high speed USB device using ehci_hcd and address 32
Aug 17 10:14:34 Vinyasa kernel: [ 7536.910546] usb 5-8: new high speed USB device using ehci_hcd and address 33
Aug 17 10:14:35 Vinyasa kernel: [ 7537.892226] usb 5-8: new high speed USB device using ehci_hcd and address 34
Aug 17 10:14:36 Vinyasa kernel: [ 7538.411005] usb 5-8: new high speed USB device using ehci_hcd and address 35




And here is the working ports:

> justin@Vinyasa:~$ tail -f /var/log/messages
Aug 17 10:19:38 Vinyasa kernel: [ 7840.186488] scsi1626 : SCSI emulation for USB Mass Storage devices
Aug 17 10:19:43 Vinyasa kernel: [ 7845.173731] scsi 1626:0:0:0: Direct-Access     LEXAR    JD FIREFLY       1100 PQ: 0 ANSI: 0 CCS
Aug 17 10:19:43 Vinyasa kernel: [ 7845.176586] SCSI device sda: 7928832 512-byte hdwr sectors (4060 MB)
Aug 17 10:19:43 Vinyasa kernel: [ 7845.177445] sda: Write Protect is off
Aug 17 10:19:43 Vinyasa kernel: [ 7845.180065] SCSI device sda: 7928832 512-byte hdwr sectors (4060 MB)
Aug 17 10:19:43 Vinyasa kernel: [ 7845.181687] sda: Write Protect is off
Aug 17 10:19:43 Vinyasa kernel: [ 7845.181709]  sda: sda1
Aug 17 10:19:43 Vinyasa kernel: [ 7845.252043] sd 1626:0:0:0: Attached scsi removable disk sda
Aug 17 10:19:43 Vinyasa kernel: [ 7845.252103] sd 1626:0:0:0: Attached scsi generic sg0 type 0
Aug 17 10:20:05 Vinyasa kernel: [ 7867.467924] usb 5-1: USB disconnect, address 60
Aug 17 10:20:19 Vinyasa kernel: [ 7881.395103] usb 5-1: new high speed USB device using ehci_hcd and address 61
Aug 17 10:20:20 Vinyasa kernel: [ 7881.528810] usb 5-1: configuration #1 chosen from 1 choice
Aug 17 10:20:20 Vinyasa kernel: [ 7881.529066] scsi1627 : SCSI emulation for USB Mass Storage devices
Aug 17 10:20:25 Vinyasa kernel: [ 7886.516430] scsi 1627:0:0:0: Direct-Access     LEXAR    JD FIREFLY       1100 PQ: 0 ANSI: 0 CCS
Aug 17 10:20:25 Vinyasa kernel: [ 7886.519140] SCSI device sda: 7928832 512-byte hdwr sectors (4060 MB)
Aug 17 10:20:25 Vinyasa kernel: [ 7886.520012] sda: Write Protect is off
Aug 17 10:20:25 Vinyasa kernel: [ 7886.522755] SCSI device sda: 7928832 512-byte hdwr sectors (4060 MB)
Aug 17 10:20:25 Vinyasa kernel: [ 7886.523628] sda: Write Protect is off
Aug 17 10:20:25 Vinyasa kernel: [ 7886.523642]  sda: sda1
Aug 17 10:20:25 Vinyasa kernel: [ 7886.593994] sd 1627:0:0:0: Attached scsi removable disk sda
Aug 17 10:20:25 Vinyasa kernel: [ 7886.594055] sd 1627:0:0:0: Attached scsi generic sg0 type 0

Only one of the USB ports on the back work, so i just copied that one...

---

### Post by Pragmatist on 2007-08-17
Notice the **sda** in the output of the working USB ports and its absence in the other port.   Let's see what HAL thinks of the ports:
```
hal-device-manager
```

Let us know what you find.

---

### Post by justin_blair on 2007-08-17
I'm not sure what your asking me, sorry but I'm pretty much a new be, can you explain to me what you want me to look at once I have Device Manager open?

---

### Post by Pragmatist on 2007-08-17
Take a look at the attached screenshots.  Both are taken from hal-device-manager (which you can run by typing this in a terminal:
```
hal-device-manager
```

In both cases I am selecting a device in the left panel and then looking at information about the device on the right side.  I have clicked the "advanced" tab and I selected the line I am most interested in:
> info.product    string    USB 1.0 Controller

---

### Post by justin_blair on 2007-08-17
Thanks, a picture is worth a thousand words!

[IMG]http://i47.photobucket.com/albums/f162/justin_blair/Screenshot-1.png[/IMG]

[IMG]http://i47.photobucket.com/albums/f162/justin_blair/Screenshot.png[/IMG]

---

### Post by Pragmatist on 2007-08-17
what is the exact model of the flash drive?

---

### Post by Pragmatist on 2007-08-17
Also, can you test the front ports by plugging in some other devices?

---

### Post by justin_blair on 2007-08-17
Lexar JD-FireFly 4GB

---

### Post by justin_blair on 2007-08-17
My USB mouse works flawlessly in both front usb ports.

---

### Post by Pragmatist on 2007-08-17
I researched this a little, and it looks like USB 2.0 is "recommended".  My guess is that this is the problem.  Here are the solutions I would consider:

1.) Try a USB 2.0 hub and connect to one of the rear, USB 2.0, ports.

2.) See if there is some extension cable available that you can plug into the back and then plug the drive into the other end.

3.) Continue researching by testing the device in the front port using another OS. I would try a LiveCD like Knoppix and I would also try Windows if possible.

USB 2.0 is much faster than USB 1.0 or USB 1.1  This speed is important when you are transferring large amounts of information, and using large drives.  Since you have a 4GB drive, it makes sense that it would work better with USB 2.0

---

### Post by justin_blair on 2007-08-17
Ok, I guess I will have to resort to using a hub or cable from the back port.  
It does work under Windows XP, but I also just updated the bios.
I reformatted it with gparted live CD, just to freshen it up.  
I think I will try a live CD next.  
If you get anymore ideas let me know.
Thanks for the support.

---

### Post by justin_blair on 2007-08-23
Well the extension cable works, I would like to be able to use those other USB ports too.  Is there someway to get the other USB ports working?

---

