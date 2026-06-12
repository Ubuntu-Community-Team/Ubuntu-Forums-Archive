---
title: "External HD and dmesg log - &quot;utf8 is not a recommended ....&quot;"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by Zar on 2006-11-19
I have partitioned my 120GB Western Digital external HD by qtparted.  dmesg says "utf8 is not a recommended ..."

Is it just a warning? or will I risk my data if I keep on using the disk.

Thank you.


[4294795.387000] usb-storage: device found at 3
[4294795.387000] usb-storage: waiting for device to settle before scanning
[4294795.387000] usbcore: registered new driver usb-storage
[4294795.387000] USB Mass Storage support registered.
[4294800.389000]   Vendor: WDC WD12  Model: 00VE-00KWT0       Rev: 0000
[4294800.389000]   Type:   Direct-Access                      ANSI SCSI revision : 00
[4294800.397000] usb-storage: device scan complete
[4294800.436000] Driver 'sd' needs updating - please use bus_type methods
[4294800.438000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[4294800.438000] sda: assuming drive cache: write through
[4294800.441000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[4294800.441000] sda: assuming drive cache: write through
[4294800.441000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 sda9 sda10 >
[4294800.581000] sd 0:0:0:0: Attached scsi disk sda
[4294800.593000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294801.864000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294802.114000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294802.389000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294802.533000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294802.675000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294802.810000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294802.986000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294803.133000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

---

### Post by b_martinez on 2006-11-19
[QUOTE=Zar;1778934]I have partitioned my 120GB Western Digital external HD by qtparted.  dmesg says "utf8 is not a recommended ..."

Is it just a warning? or will I risk my data if I keep on using the disk.

Thank you.


[4294795.387000] usb-storage: device found at 3
[4294795.387000] usb-storage: waiting for device to settle before scanning
[4294795.387000] usbcore: registered new driver usb-storage
[4294795.387000] USB Mass Storage support registered.
[4294800.389000]   Vendor: WDC WD12  Model: 00VE-00KWT0       Rev: 0000
[4294800.389000]   Type:   Direct-Access                      ANSI SCSI revision : 00
[4294800.397000] usb-storage: device scan complete
[4294800.436000] Driver 'sd' needs updating - please use bus_type methods
[4294800.438000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[4294800.438000] sda: assuming drive cache: write through
[4294800.441000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[4294800.441000] sda: assuming drive cache: write through
[4294800.441000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 sda9 sda10 >
[4294800.581000] sd 0:0:0:0: Attached scsi disk sda
[4294800.593000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294801.864000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294802.114000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294802.389000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294802.533000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294802.675000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294802.810000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294802.986000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294803.133000] FAT: utf8 is not a recommended IO charset for FAT filesystems,  filesystem will be case sensitive!

Just means that you need to realize that files like My_Pix, My_PIX, My_pix, and my_pix will all be different .
That's what this means. ---> "filesystem will be case sensitive!" 
It also works for folders. so you can have a LOT of folders named something along the lines of "my_music".
hth
Bill

---

### Post by Zar on 2006-11-20
> **b_martinez said:**
> 
Just means that you need to realize that files like My_Pix, My_PIX, My_pix, and my_pix will all be different .
That's what this means. ---> "filesystem will be case sensitive!" 
It also works for folders. so you can have a LOT of folders named something along the lines of "my_music".
hth
Bill

Thank you very much.  I wanted to make sure.  I am bit paranoid about my data.

---

