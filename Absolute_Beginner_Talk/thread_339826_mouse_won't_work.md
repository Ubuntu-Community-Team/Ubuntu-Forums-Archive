---
title: "mouse won't work"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by jctaft on 2007-01-16
Hi everyone, I imagine this is probably a very basic problem.  My laptop touch mouse works fine, except that I hate it, and have always carried around a normal mouse which plugs into my USB port.  It doesn't work, however on my Ubuntu system.  I have checked that the USB port works by plugging a drive into it, and I have verified that the mouse works by plugging it into a different computer running Ubuntu.  

The output of lsusb is

Bus 001 Device 001: ID 0000:0000

The mouse is called a "basic optical mouse" by microsoft.

Any ideas?

---

### Post by earobinson on 2007-01-16
unplug it and plug it back in.

also can you post the tail of your /var/log/messages ```
tail /var/log/messages 
```

---

### Post by jctaft on 2007-01-16
unplugging/pluggin didn't work, nor did trying any of my other USB ports.

The output:

jeff@jeff-laptop:~$ tail /var/log/messages
Jan 16 08:57:09 jeff-laptop kernel: [ 4976.750221] sda: Write Protect is off
Jan 16 08:57:09 jeff-laptop kernel: [ 4976.750244]  sda: sda1
Jan 16 08:57:09 jeff-laptop kernel: [ 4976.751782] sd 4:0:0:0: Attached scsi removable disk sda
Jan 16 08:57:09 jeff-laptop kernel: [ 4976.751868] sd 4:0:0:0: Attached scsi generic sg0 type 0
Jan 16 08:57:09 jeff-laptop kernel: [ 4976.759345] sr0: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
Jan 16 08:57:09 jeff-laptop kernel: [ 4976.759501] sr 4:0:0:1: Attached scsi generic sg1 type 5
Jan 16 08:57:13 jeff-laptop kernel: [ 4982.198814] UDF-fs: No VRS found
Jan 16 08:57:13 jeff-laptop kernel: [ 4982.228806] UDF-fs: No VRS found
Jan 16 08:59:30 jeff-laptop kernel: [ 5120.370958] usb 1-3: USB disconnect, address 16
Jan 16 08:59:30 jeff-laptop kernel: [ 5120.378498] VFS: busy inodes on changed media.

---

