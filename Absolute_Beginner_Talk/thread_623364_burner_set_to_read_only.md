---
title: "burner set to read only?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Ubukanuba on 2007-11-25
my dvd/cd recorder is set to read only and when i try to right click the drive>properties>permissions it wont allow me to change it to read and write. All three options are set to read only. I get this error when i check read/write:

"permissions could not be changed- Sorry, couldn't change the permissions of "CD-RW/DVD±RW Drive"."

What do I do?? Thanks!

---

### Post by jfinkels on 2007-11-26
Have you put in a writable CD or DVD? What happens when you try to write to a disc?

---

### Post by Ubukanuba on 2007-11-27
nothing it sometimes will spin for a second...but it wont even mount a blank disc...my dvd's and audio/data cd's all are working perfectly....Just cant burn.

---

### Post by jfinkels on 2007-11-27
What error message do you get when you mount the device from the terminal? Type:```
sudo mount /dev/cdrom
```

---

### Post by Ubukanuba on 2007-11-28
> mount: block device /dev/hda is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


this is what i get

---

### Post by jfinkels on 2007-11-29
Are you sure you are putting in a blank CD-R or CD-RW? What is the output of ```
dmesg|tail
``` after trying to mount the drive?

---

### Post by Ubukanuba on 2007-11-30
> [   42.000297] Bluetooth: RFCOMM TTY layer initialized
[   42.000299] Bluetooth: RFCOMM ver 1.8
[   47.262797] NET: Registered protocol family 17
[   49.742457] NET: Registered protocol family 10
[   49.742656] lo: Disabled Privacy Extensions
[   59.849336] eth0: no IPv6 routers present
[  100.328834] hda: DMA timeout retry
[  100.328839] hda: timeout waiting for DMA
[  425.141347] audit(1196454175.708:6):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=6239 profile="/usr/sbin/cupsd"
[  425.162859] audit(1196454175.732:7):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=6242 profile="/usr/sbin/cupsd"


yeah tried both dvd and cd got this

---

### Post by NightCrawler03X on 2007-12-04
This happened for me too.

Then I remembered that ubuntu automounts cd/dvd.
You need raw access, that is, they can't be mounted.

If, for example, you have a dvd in a dvd-rom drive, and a blank dvd in a dvdrw drive, unmount the two drives:

Go to your terminal
```
umount /dev/scd0
umount /dev/scd1
```
The "/dev/scd0" and "/dev/scd1" might be different for you (that is, you have a different file controlling your drives.

Most, if not all, cd/dvd authoring software on linux requires RAW access the any drive your using, so you *must* unmount the drives you wish to use, first.

Regards

---

