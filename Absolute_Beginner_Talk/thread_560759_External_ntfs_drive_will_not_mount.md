---
title: "External ntfs drive will not mount"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by rude_lee on 2007-09-26
i have an external drive that will not mount i keep getting a mount error
it used to mount fine then it mounted read only tried ntfs-config it did not give me write support at all so in the properties of the drive i put something in like read/write now it wont mount at all all i get is the mount error 
how do i fix this 

 fdisk -l
gives me
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11808    94847728+  83  Linux
/dev/hda2           11809       12161     2835472+   5  Extended
/dev/hda5           11809       12161     2835441   82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

dmesg gives me
[  580.716000] usb 3-4: new high speed USB device using ehci_hcd and address 3
[  580.848000] usb 3-4: configuration #1 chosen from 1 choice
[  581.068000] usbcore: registered new interface driver libusual
[  581.092000] Initializing USB Mass Storage driver...
[  581.092000] scsi0 : SCSI emulation for USB Mass Storage devices
[  581.092000] usbcore: registered new interface driver usb-storage
[  581.092000] USB Mass Storage support registered.
[  581.092000] usb-storage: device found at 3
[  581.092000] usb-storage: waiting for device to settle before scanning
[  586.092000] usb-storage: device scan complete
[  586.092000] scsi 0:0:0:0: Direct-Access     ST350064 1AS              E    PQ: 0 ANSI: 2 CCS
[  586.144000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[  586.144000] sda: Write Protect is off
[  586.144000] sda: Mode Sense: 00 38 00 00
[  586.144000] sda: assuming drive cache: write through
[  586.148000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[  586.148000] sda: Write Protect is off
[  586.148000] sda: Mode Sense: 00 38 00 00
[  586.148000] sda: assuming drive cache: write through
[  586.148000]  sda: sda1
[  586.164000] sd 0:0:0:0: Attached scsi disk sda
[  586.188000] sd 0:0:0:0: Attached scsi generic sg0 type 0

need help bad really want this to work its pissing me off cuse i reformated and lost allmy stuff on there to see if it will work no dice

---

### Post by Pumalite on 2007-09-26
Use rescuecd: [http://www.sysresccd.org/Download.en.php](http://www.sysresccd.org/Download.en.php)
[http://www.sysresccd.org/Online-Manual-EN](http://www.sysresccd.org/Online-Manual-EN), to check your drive.
What did you use to reformat?

---

### Post by voided3 on 2007-09-26
Also, if you a have Windows XP computer handy, hook it up to that and run a try running a disk check with the "fix" option enabled. However, if it won't mount on Windows, then the problem lies elsewhere. Good luck!

---

### Post by rude_lee on 2007-09-26
i used g partition manager but i dont care about that i need the drive to mount first anyway and have write support

---

### Post by Pumalite on 2007-09-26
Do the checking and report back then.

---

### Post by rude_lee on 2007-09-26
were do you press to do the disk check

---

### Post by rude_lee on 2007-09-26
nope did not work still giving me invalid mount option
anyway to make it mount as read only to change settings back or at least to change its properties

---

