---
title: "write-protected sony digital camera"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-06-29
im connecting my sony digicam (syber-shot dsc-s650) to my laptop via the usb cable but it seems impossible to write to the camera (so i can delete photos)

syslog output
```

Jun 29 14:51:40 pete-laptop kernel: [ 6566.264000] scsi 7:0:0:0: Direct-Access     SONY     DSC              1.10 PQ: 0 ANSI: 0 CCS
Jun 29 14:51:40 pete-laptop kernel: [ 6566.276000] SCSI device sda: 49343 512-byte hdwr sectors (25 MB)
Jun 29 14:51:40 pete-laptop kernel: [ 6566.280000] sda: Write Protect is on


```


so i then tried to manually mount it as rw, heres the results of that
```

$ sudo mount -t vfat -o shortname=win95,check=s /dev/sda1 /media/iso
mount: block device /dev/sda1 is write-protected, mounting read-only

```


any ideas? i can read/write when using windows to connect.

---

### Post by aeiah on 2007-06-29
this can happen if the card is slightly corrupted and does it for safeties sake. i had problems like that when plugging in my nokia 770. it may very well be that the card is fine and its some odd little bug though, because once i started using a standalone card reader i never got those problems again.

its probably best to format the card, and see if that helps. make sure you backup first of course and use gparted to format it.

---

### Post by PetePete on 2007-06-29
i can't use gparted, it doesn't show up... also I wouldn't be able to format it as its read-only!

---

### Post by kelvin spratt on 2007-06-29
are you talking about a SD card if so i had the same when i first started you have to eject the card before removing it or it will Write protect its sell, you are supposed to do the same in windows, but nobody bothers
just format it in your cam and it should work, also you should only delete in your cam as you can run the risk of contamination from your laptop.

---

