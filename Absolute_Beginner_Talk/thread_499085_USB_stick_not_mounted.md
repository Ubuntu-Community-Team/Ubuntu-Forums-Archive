---
title: "USB stick not mounted"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by netyire on 2007-07-12
PROBLEM RESOLVED - THANKS ALL!
Solution: Formatting the drive with mkdosfs -F 32 instead of mkdosfs made all the problems go away. (Now how was I to know?)

Hi all, I'm having problems with a certain USB stick. (Thumb drive?) When the system first starts, plugging it in works great, the files are recognized and everything is okay. However, once you eject it (right click -> unmount) and ubuntu notes that it is safe to remove the USB stick, it is not mounted when you plug it in again 5 minutes later.

Anyone have ideas on how to solve this, (preferable without rebooting :D)?

Here's the output from dmesg:
```

[12296.419010] usb 4-2: USB disconnect, address 4
[12303.716876] usb 4-2: new full speed USB device using uhci_hcd and address 5
[12303.894729] usb 4-2: configuration #1 chosen from 1 choice
[12303.897767] scsi5 : SCSI emulation for USB Mass Storage devices
[12303.897952] usb-storage: device found at 5
[12303.897956] usb-storage: waiting for device to settle before scanning
[12308.898115] usb-storage: device scan complete
[12308.901108] scsi 5:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[12309.356571] SCSI device sdb: 2012160 512-byte hdwr sectors (1030 MB)
[12309.361562] sdb: Write Protect is off
[12309.361567] sdb: Mode Sense: 03 00 00 00
[12309.361571] sdb: assuming drive cache: write through
[12309.373549] SCSI device sdb: 2012160 512-byte hdwr sectors (1030 MB)
[12309.378542] sdb: Write Protect is off
[12309.378547] sdb: Mode Sense: 03 00 00 00
[12309.378551] sdb: assuming drive cache: write through
[12309.378555]  sdb:<6>sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[12310.408413]     <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[12310.408426] end_request: I/O error, dev sdb, sector 0
[12310.408433] Buffer I/O error on device sdb, logical block 0
[12311.438262] sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[12311.438272]     <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[12311.438283] end_request: I/O error, dev sdb, sector 0
[12311.438290] Buffer I/O error on device sdb, logical block 0
[12312.468119] sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[12312.468130]     <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[12312.468141] end_request: I/O error, dev sdb, sector 0
[12312.468147] Buffer I/O error on device sdb, logical block 0
[12313.498976] sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[12313.498987]     <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[12313.498998] end_request: I/O error, dev sdb, sector 0
[12313.499004] Buffer I/O error on device sdb, logical block 0
[12314.529832] sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[12314.529843]     <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[12314.529854] end_request: I/O error, dev sdb, sector 0
[12314.529860] Buffer I/O error on device sdb, logical block 0
[12314.529876] ldm_validate_partition_table(): Disk read failed.
[12315.560688] sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[12315.560698]     <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[12315.560709] end_request: I/O error, dev sdb, sector 0
[12315.560714] Buffer I/O error on device sdb, logical block 0
[12316.591548] sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[12316.591558]     <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[12316.591569] end_request: I/O error, dev sdb, sector 0
[12316.591587] Buffer I/O error on device sdb, logical block 0
[12317.622403] sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[12317.622414]     <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[12317.622425] end_request: I/O error, dev sdb, sector 0
[12317.622430] Buffer I/O error on device sdb, logical block 0

```

---

### Post by Al3xK3aton on 2007-07-12
I'm not really clear on why you are ejecting it in the first place. Can't you just leave it in there? Also, are you a hundred percent certain that it's only when you use it the first time that it works and only when you try again that it doesn't work? Maybe the problem is the usb port, not a software problem. One of the things a lot of people run the risk of doing is blaming the software when there is a hardware malfunction. I would suggest you do a little searching on the web to see if other people using this brand/model of usb stick are having similar problems, and also to see if there is a recall on the product. 

If all else fails, you could exchange your usb card and see if a newer one works better. (Make sure the new one is usb 2.0)

---

### Post by Inxsible on 2007-07-12
You should use pmount to mount it. pmount will mount it under /media and will automatically mount it every time you connect it.
if you don't have pmount installed already
```
sudo aptitude install pmount
```

use it as follows:
```
sudo pmount /dev/Xd*? MOUNT_POINT
```where X = s or h
* = a,b,c....
? = 1,2,3....

MOUNT_POINT could be a name of your choosing provided you do not already have that folder under /media. eg. MyUSBDrive or 2GBDrive etc. pmount actually creates the folder for you.

---

### Post by netyire on 2007-07-13
Thanks for the replies! I'm unmounting the device so that I can place it in a handheld device (theres a card slot there). I'm quite sure that it worked the first time, then I unmounted it, waited a while, pluggin it back in and viola it doesn't work :D. Any ideas how to get pmount to do the mounting instead of the normal system mounting it.

Anyway heres the dmesg output when it does work:

```

[ 1143.546395] usb 4-2: new full speed USB device using uhci_hcd and address 2
[ 1143.724250] usb 4-2: configuration #1 chosen from 1 choice
[ 1143.903177] usbcore: registered new interface driver libusual
[ 1143.943337] Initializing USB Mass Storage driver...
[ 1143.945737] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1143.946043] usbcore: registered new interface driver usb-storage
[ 1143.946361] USB Mass Storage support registered.
[ 1143.946710] usb-storage: device found at 2
[ 1143.946714] usb-storage: waiting for device to settle before scanning
[ 1148.943387] usb-storage: device scan complete
[ 1148.946382] scsi 2:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[ 1149.401855] SCSI device sdb: 2012160 512-byte hdwr sectors (1030 MB)
[ 1149.406847] sdb: Write Protect is off
[ 1149.406852] sdb: Mode Sense: 03 00 00 00
[ 1149.406857] sdb: assuming drive cache: write through
[ 1149.418833] SCSI device sdb: 2012160 512-byte hdwr sectors (1030 MB)
[ 1149.423829] sdb: Write Protect is off
[ 1149.423834] sdb: Mode Sense: 03 00 00 00
[ 1149.423838] sdb: assuming drive cache: write through
[ 1149.423842]  sdb: sdb1
[ 1149.430913] sd 2:0:0:0: Attached scsi removable disk sdb
[ 1149.430977] sd 2:0:0:0: Attached scsi generic sg3 type 0

```

When it does not work, fdisk -l doesn't make anything show up. lsusb displays the device as alcor corp disk (kinda weird, I thought alcor was in the cryogenics department) or something like that. Works on windows though. Furthermore, when it fails to work, typing sudo umount /dev/sda1 simply results in a messege stating that the device is busy, nothing else works after that. Trying to mount the device again results in a system messege stating that the device is already mounted at /. Opening the / filesystem doesn't reveal anything on the card I think, although the device appears to be constantly busy. Pmount doesn't get a chance to work. Thus, pmount doesn't really do much of anything, thanks for the tip though!

I guess restarting isn't the end of the world :D, though getting it to work will be great. Knowing why it isn't working is also something good, I've done some googling and have searched the forums, apparently this problem may have something to do with a grub option at boot or something.

If you gals and guys have any ideas please let me know.

---

