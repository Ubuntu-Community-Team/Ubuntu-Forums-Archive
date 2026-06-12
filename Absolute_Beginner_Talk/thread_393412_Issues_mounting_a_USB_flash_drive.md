---
title: "Issues mounting a USB flash drive"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by fusiachi on 2007-03-25
I've been using this flash drive for a while, but today for some reason it won't mount on my machine.  Works fine on other computers.  When I try to access it, an error pops up: ```
error: libhal_ctx_init: (null): (null)
```

No clue what this means.  Output from **dmesg | tail**
```

[17255043.520000] sda: Write Protect is off
[17255043.520000] sda: Mode Sense: 23 00 00 00
[17255043.520000] sda: assuming drive cache: write through
[17255043.528000] SCSI device sda: 1007616 512-byte hdwr sectors (516 MB)
[17255043.528000] sda: Write Protect is off
[17255043.528000] sda: Mode Sense: 23 00 00 00
[17255043.528000] sda: assuming drive cache: write through
[17255043.528000]  sda: sda1
[17255043.532000] sd 3:0:0:0: Attached scsi removable disk sda
[17255043.532000] sd 3:0:0:0: Attached scsi generic sg0 type 0

```

Any help would be greatly appreciated.

Thanks,

Wade

---

### Post by tatimmer on 2007-03-29
I had a similar problem where my pen drive was detected and mounted just fine for a while then all of a sudden stopped. It appears your kernel detects the device but then mayby "HAL" is falling down on the job.

My solution is to just manual mount:
sudo mount -t vfat /dev/sda1 /media/usb

I have a script on my website and also a gtk dialog with pushbuttons to do the same.

---

