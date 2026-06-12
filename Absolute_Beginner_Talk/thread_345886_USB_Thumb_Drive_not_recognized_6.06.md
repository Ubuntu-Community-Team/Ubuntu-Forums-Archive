---
title: "USB Thumb Drive not recognized 6.06"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by LordStryker on 2007-01-24
I am a linux and Ubuntu noob so I dont know where to start.  I just installed ubuntu and my usb thumb drive is not recognized.  I dont know what commands to enter to start to troubleshoot this, and the ethernet also doesnt work.  It only has wireless so I went and got the windows .inf file on the thumb drive to try ndiswrapper so I could try and get the wireless working.  But first, I need the usb working and I dont know where to start.  I've tried googling for topics on unrecognized usb drives but didnt find much.  I know the drive itself is OK as I put Ubuntu on a laptop and it sees the thumb drive just fine.  Any suggestions would be greatly appreciated.

---

### Post by riven0 on 2007-01-25
Try plugging in your usb drive, then go to the terminal and copy and paste this command:

> sudo fdisk -l

Then post the results

---

### Post by LordStryker on 2007-01-25
Since I have no internet on that computer, I'll copy the output from a "sudo fdisk -l"

Disk /dev/hda:  30.0 GB,  30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device     Boot        Start              End        Blocks       Id     System
/dev/hda1     *          1                    3497       28089621   83     Linux 
/dev/hda2                 3498              3649        1220940    5       Extended
/dev/hda5                 3498              3649        1220908+  82     Linux swap / Solaris

Disk /dev/hdb:    30.7 GB,    3073581184 bytes
255 heads, 63 sectors/track,  3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

     Device   Boot     Start               End          Blocks          Id     System
/dev/hdb1     *           1                 3736         30009388+   86    Linux LVM





Thats it.  I have 2 hard disks, hence the hdb, though I dont know where it is or how to access that being a linux noob, but I'll deal with that later.

---

### Post by yabbadabbadont on 2007-01-25
Plug in the usb drive, then run "dmesg | grep -i usb".  If possible, post the output, but look for any error messages or warnings.

---

### Post by LordStryker on 2007-01-25
Output for "dmesg | grep -i usb"

[17179575,908000]  PCI0  USB0  USB1  MODM  UAR1  UAR2  LPT1




Thats it

---

### Post by yabbadabbadont on 2007-01-25
It looks like the usb modules aren't being loaded automagically like they should be...  try removing the usb drive then running, "sudo modprobe usb_storage", then plug it back in and run the dmesg command I gave you.  Hopefully, you will see something like:
> [17191753.996000] usb 1-4: new high speed USB device using ehci_hcd and address 4
[17191754.184000] Initializing USB Mass Storage driver...
[17191754.184000] scsi3 : SCSI emulation for USB Mass Storage devices
[17191754.184000] usb-storage: device found at 4
[17191754.184000] usb-storage: waiting for device to settle before scanning
[17191754.184000] usbcore: registered new driver usb-storage
[17191754.184000] USB Mass Storage support registered.
[17191759.184000]   Vendor: SanDisk   Model: Cruzer Micro      Rev: 0.4 
[17191759.184000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17191759.188000] SCSI device sdb: 1000944 512-byte hdwr sectors (512 MB)
[17191759.188000] sdb: Write Protect is off
[17191759.188000] sdb: Mode Sense: 03 00 00 00
[17191759.188000] sdb: assuming drive cache: write through
[17191759.188000] SCSI device sdb: 1000944 512-byte hdwr sectors (512 MB)
[17191759.188000] sdb: Write Protect is off
[17191759.188000] sdb: Mode Sense: 03 00 00 00
[17191759.188000] sdb: assuming drive cache: write through
[17191759.188000]  sdb: sdb1
[17191759.192000] sd 3:0:0:0: Attached scsi removable disk sdb
[17191759.192000] sd 3:0:0:0: Attached scsi generic sg1 type 0
[17191759.192000] usb-storage: device scan complete


---

### Post by LordStryker on 2007-01-25
Ok, did that.  here's what I get now:

[17179575,908000] PCI0 USB0 USB1 MODM UAR1 UAR2 LPT1
[17187810,716000] usbcore: registered new driver usbfs
[17187810,716000] usbcore: registered new driver hub
[17187810,784000] initializing USB Mass Storage driver...
[17187810,788000] usbcore: registered new driver usb-storage
[17187810,716000] USB Mass Storage support registered



Thats it

---

