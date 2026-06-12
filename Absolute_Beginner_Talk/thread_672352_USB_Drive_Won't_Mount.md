---
title: "USB Drive Won't Mount"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by weaver4 on 2008-01-19
My usb flash drive won't mount.

I do a lsusb and it shows up, but it never gets mounted.

The usb drive is formated to Fat32 and it works fine in a Windows Box.  Also tested with a FAT usb drive and it also failed.

Here are the last few lines from the dmesg command.

[ 1176.543345] usb 5-4: new high speed USB device using ehci_hcd and address 8
[ 1176.677099] usb 5-4: config 1 has an invalid descriptor of length 0, skipping remainder of the config
[ 1176.677177] usb 5-4: config 1 interface 0 altsetting 0 has an invalid endpoint with address 0xFF, skipping
[ 1176.677212] usb 5-4: config 1 interface 0 altsetting 0 has 1 endpoint descriptor, different from the interface descriptor's value: 2
[ 1176.680596] usb 5-4: configuration #1 chosen from 1 choice
[ 1176.681747] usb-storage: probe of 5-4:1.0 failed with error -5
[ 1862.318106] usb 5-4: USB disconnect, address 8
[ 1876.241391] usb 5-4: new high speed USB device using ehci_hcd and address 9
[ 1876.378068] usb 5-4: configuration #1 chosen from 1 choice
[ 1876.379904] scsi5 : SCSI emulation for USB Mass Storage devices
[ 1876.382836] usb-storage: device found at 9
[ 1876.382877] usb-storage: waiting for device to settle before scanning
[ 1881.371613] usb-storage: device scan complete
[ 1881.482928] usb 5-4: reset high speed USB device using ehci_hcd and address 9
[ 1881.619005] scsi 5:0:0:0: Direct-Access     LEXAR    JD TRAVELER      1000 PQ: 0 ANSI: 0 CCS
[ 1881.738434] usb 5-4: reset high speed USB device using ehci_hcd and address 9

---

### Post by ryanVickers on 2008-01-19
well, I don't know exactly what it all means, if its a Linux thing, partition problem, connection problem, or hardware problem, but regardless, there are several errors there that would end up making it not work, as it says in line 7 ( [ 1862.318106] usb 5-4: USB disconnect, address 8 )

---

### Post by weaver4 on 2008-01-19
Don't know why though, dual boot system and windows works fine.  So it is not a USB Drive problem, it is not a hardware problem, so it sounds like a Ubuntu Problem.

---

### Post by ryanVickers on 2008-01-19
most likely, your right then...

It's interesting that its having a problem; a flash drive is pretty standard technology, it should work!
I can see possible problems if it was a HDD through USB, but not a flash drive... :mad:

---

### Post by Majorix on 2008-01-19
You might have to edit your /etc/fstab to include the UUID and mount points etc for your device. That would most likely solve it, but I don't know why you would have that problem in the first place.

---

### Post by ryanVickers on 2008-01-19
keep in mind that temporary devices that come and go (like USB stuff) will go under "mtab" - fstab is for static info, like internal drives...

---

### Post by kwacka on 2008-01-19
Try removing all usb drives, then delete /media/.hal-mtab

Might be best to restart.

---

### Post by Majorix on 2008-01-19
> **ryanVickers said:**
> keep in mind that temporary devices that come and go (like USB stuff) will go under "mtab" - fstab is for static info, like internal drives...

For me USB drives can be stacked in fstab too. You have to know the UUID's though.

---

### Post by weaver4 on 2008-01-19
It does not work with any USB drive, tried three, or my camera.

---

### Post by weaver4 on 2008-01-19
And it did not work on the LiveCD either.

---

### Post by weaver4 on 2008-01-19
I would not know how to modify the fstab file.

---

### Post by Majorix on 2008-01-19
First do this, and save the resulting uuid somewhere:
```
ls -l /dev/disk/by-uuid/
```
Then edit fstab
```
gksudo gedit /etc/fstab
```
There, add this info:
> UUID=your_uuid	mount_location(make sure it exists)  vfat	defaults	0	0
When you restart and come back, you should be able to mount your device without problems.

---

### Post by weaver4 on 2008-01-19
The only entry I got was one that looks like this.  Which I think are harddrives.  The USB drives were plugged in.

ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-01-19 18:00 0186358b-5606-479a-bc76-e9313f1969db -> ../../hda1
lrwxrwxrwx 1 root root 10 2008-01-19 18:00 2e309dba-1ec9-4a86-9aa1-59cee6e5350b -> ../../hda5

---

### Post by billgoldberg on 2008-01-19
Try a different usb port, maybe on the back of the computer.

That could just fix it (it did for me)

---

### Post by weaver4 on 2008-01-19
Nope, did not fix it.

---

### Post by johnnyhop on 2008-03-31
Did you ever get your usb drive to mount?  I was having the same problem on the second computer I installed Kubuntu on.  The other install doesn't require a mount command, just plug it in and an icon comes up on the desktop and in storage media.  On the second computer I was having the same problem you had posted on 1/19.  What worked for me took some experimenting in fstab and with the mount command.  Ultimately what worked was removing the reference in fstab and using the UUID in the mount command like so:  sudo mount -t vfat -U 3B69-1AFD /media/usbdrv.  When umount is done remove the -U and UUID.

The same computer on which I had to go to some trouble to get the USB drive to work the USB drive worked seamlessly on 8.04 beta.

---

