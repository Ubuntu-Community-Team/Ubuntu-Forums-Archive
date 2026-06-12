---
title: "HowTo reload USB DVD drive after DVD power cycle"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by bboons on 2007-07-30
I'm running Xubuntu 7.04 and I have a working LITEON USB external DVD writer. The drive works fine when I plug it in. But what I really want to do is to leave the DVD burner plugged into the computer's USB port and power down the DVD drive and power it up only when needed. For some reason after I power it down and then back up nothing happens.
Here's the output from dmesg:
[191155.027316] usb 4-2: USB disconnect, address 8
[191155.028468] scsi 0:0:0:0: scsi: Device offlined - not ready after error recovery
[191155.065389] scsi 0:0:0:0: rejecting I/O to dead device
[191155.065700] scsi 0:0:0:0: rejecting I/O to dead device
[191155.065720] scsi 0:0:0:0: rejecting I/O to dead device
[191155.065744] scsi 0:0:0:0: rejecting I/O to dead device
[191155.065774] scsi 0:0:0:0: rejecting I/O to dead device
[191155.065794] scsi 0:0:0:0: rejecting I/O to dead device

If I unplug and re-plug the USB then the drive comes back up but I'd rather not keep playing around with the USB connector if there is a way to do the equivalent from command-line. So, what I'm looking for is some sort of a device restart command that will reload the drive.

Thanks.

---

### Post by bboons on 2007-08-01
bump.

---

### Post by bboons on 2007-11-14
Still looking for an answer :(
Anybody?!

---

