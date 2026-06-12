---
title: "USB Flash Drive wont mount"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by tatimmer on 2006-08-30
My usb flash drive hotplug was working fine for a month but last night while my daughter was chatting away on the internet, It stopped working.

Before when you plugged in the device and a folder "/media/usbdisk" was created along with an icon on the desktop and I could view the contents of the flash drive in this folder.

Now when you plug in the device, no icon is created on the desktop, but  Nautilus->Computer shows an icon called "Simple Flash Disk 2.0" but when I try to double click on this it says "Unable to mount the selected volume, given UDI is not a mountable volume."


It appears the device is detected fine, but not mounted properly.
Any ideas on how to fix it ?

Thanks.

************************************************************************

When I plug in the device, "tail -f /var/log/messages" reports:

Aug 30 06:52:09 localhost kernel: [4302338.935000] usb 1-1: new full speed USB device using uhci_hcd and address 10
Aug 30 06:52:10 localhost kernel: [4302339.044000] scsi8 : SCSI emulation for USB Mass Storage devices
Aug 30 06:52:10 localhost usb.agent[13230]:      usb-storage: already loaded
Aug 30 06:52:14 localhost kernel: [4302344.053000]   Vendor: Simple    Model: Flash Disk 2.0    Rev: 2.00
Aug 30 06:52:14 localhost kernel: [4302344.053000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Aug 30 06:52:15 localhost kernel: [4302344.640000] SCSI device sda: 505856 512-byte hdwr sectors (259 MB)
Aug 30 06:52:15 localhost kernel: [4302344.643000] sda: Write Protect is off
Aug 30 06:52:15 localhost kernel: [4302344.662000] SCSI device sda: 505856 512-byte hdwr sectors (259 MB)
Aug 30 06:52:15 localhost kernel: [4302344.664000] sda: Write Protect is off
Aug 30 06:52:15 localhost kernel: [4302344.665000]  /dev/scsi/host8/bus0/target0/lun0: p1
Aug 30 06:52:15 localhost kernel: [4302344.677000] Attached scsi removable disk sda at scsi8, channel 0, id 0, lun 0
Aug 30 06:52:16 localhost scsi.agent[13279]:      sd_mod: loaded sucessfully (for disk)

---

### Post by PPAAUULL on 2006-08-30
Have you tryed Googleing something on it. When I look through the log it seems to be fine but I also see no mention of "UDI". I would look that up. I will look around and see what I can  find:-k .

Also have you tryed to mount it in the terminal? that might work aswell.

Paul

---

### Post by PPAAUULL on 2006-08-30
Ok I think I might have found a solution for you. Take a look at this thread and try it on your USB stick. It should work: [http://www.ubuntuforums.org/showthread.php?t=76517](http://www.ubuntuforums.org/showthread.php?t=76517). I knew it should be some kind of mount command. I hope that helps.

Paul

---

### Post by tatimmer on 2006-08-30
Thanks for your reply. I will try this tonight.  I also have the same problem with the floppy (will not automount).  I dont use the floppy much so went I do I just mount manually.

---

### Post by PPAAUULL on 2006-08-30
I hope it works for you.

---

