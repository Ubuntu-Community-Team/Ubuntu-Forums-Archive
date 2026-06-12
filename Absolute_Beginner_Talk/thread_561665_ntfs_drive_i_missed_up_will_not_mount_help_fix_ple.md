---
title: "ntfs drive i missed up will not mount help fix please"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by rude_lee on 2007-09-27
i have an external drive that will not mount i keep getting a mount error
it used to mount fine then it mounted read only tried ntfs-config it did not give me write support at all so in the properties of the drive i put something in like read/write now it wont mount at all all i get is the mount error
how do i fix this

fdisk -l
gives me
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 11808 94847728+ 83 Linux
/dev/hda2 11809 12161 2835472+ 5 Extended
/dev/hda5 11809 12161 2835441 82 Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 60801 488384001 7 HPFS/NTFS

dmesg gives me
[ 580.716000] usb 3-4: new high speed USB device using ehci_hcd and address 3
[ 580.848000] usb 3-4: configuration #1 chosen from 1 choice
[ 581.068000] usbcore: registered new interface driver libusual
[ 581.092000] Initializing USB Mass Storage driver...
[ 581.092000] scsi0 : SCSI emulation for USB Mass Storage devices
[ 581.092000] usbcore: registered new interface driver usb-storage
[ 581.092000] USB Mass Storage support registered.
[ 581.092000] usb-storage: device found at 3
[ 581.092000] usb-storage: waiting for device to settle before scanning
[ 586.092000] usb-storage: device scan complete
[ 586.092000] scsi 0:0:0:0: Direct-Access ST350064 1AS E PQ: 0 ANSI: 2 CCS
[ 586.144000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[ 586.144000] sda: Write Protect is off
[ 586.144000] sda: Mode Sense: 00 38 00 00
[ 586.144000] sda: assuming drive cache: write through
[ 586.148000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[ 586.148000] sda: Write Protect is off
[ 586.148000] sda: Mode Sense: 00 38 00 00
[ 586.148000] sda: assuming drive cache: write through
[ 586.148000] sda: sda1
[ 586.164000] sd 0:0:0:0: Attached scsi disk sda
[ 586.188000] sd 0:0:0:0: Attached scsi generic sg0 type 0

need help bad really want this to work its pissing me off cuse i reformated and lost allmy stuff on there to see if it will work no dice

---

### Post by frafu on 2007-09-29
Hello, 

I am moving this thread to the Absolute Beginner Forum, where it might have a better chance to get replies, as the Accessibility Forum is normally used for disability related software. 

Moreover, if you are in hurry, you might want to do some searches in the [Forums]("http://ubuntuforums.org/index.php") and in the [Wiki]("https://wiki.ubuntu.com/"), by using the search box at the top right of the page. 

For example a search in the forums with the keywords 'ntfs mount problems' turned out (among others) the following thread: 
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Cheers 

Francesco

---

