---
title: "mount question"
date: 2012-07-03
forum: Any Other OS
---

### Post by Drenriza on 2012-07-03
Hey guys.

I have a device as such
[6173721.285002] SCSI device sdc: 62734336 512-byte hdwr sectors (32120 MB)
[6173721.285628] sdc: Write Protect is off
[6173721.285663] sdc: Mode Sense: 23 00 00 00
[6173721.285666] sdc: assuming drive cache: write through
[6173721.285705]  sdc: sdc1

when i then say
```
mount /dev/sdc1 /mnt
```
i get this error.
mount: you must specify the filesystem type

Does the system think that the filesystem on the usb stick is corrupt? Or why do you / i get such an error?

Thanks on advance.
Kind regards.

---

### Post by SeijiSensei on 2012-07-03
Yes, that error means Linux can't find a filesystem on the device.  Are you sure it's formatted?  Does it work with Windows but not Linux?

---

### Post by Cheesemill on 2012-07-03
Also can you post the output of:
```
sudo fdisk -l /dev/sdc
```

---

### Post by Drenriza on 2012-07-03
> **SeijiSensei said:**
> Yes, that error means Linux can't find a filesystem on the device.  Are you sure it's formatted?  Does it work with Windows but not Linux?

The device was formatted on a Debian Lenny system, mounted and files transferred to it. But now when it arrives at it's destination, also a Lenny system. I get this error when trying to mount.

---

### Post by cortman on 2012-07-03
> **Drenriza said:**
> The device was formatted on a Debian Lenny system, mounted and files transferred to it. But now when it arrives at it's destination, also a Lenny system. I get this error when trying to mount.

Are you even able to mount a device to /mnt? I always thought you needed to create a subdirectory in /mnt and mount it to there.

```
sudo mkdir /mnt/usb
sudo mount /dev/sdc1 /mnt/usb
```

---

### Post by sudodus on 2012-07-03
... or try
```
sudo mkdir /mnt/usb
sudo mount -t auto /dev/sdc1 /mnt/usb
```

And it might be easier to help if you post the output of
```
sudo fdisk -lu /dev/sdc
```

---

### Post by coffeecat on 2012-07-03
> **Drenriza said:**
> The device was formatted on a Debian Lenny system, mounted and files transferred to it. But now when it arrives at it's destination, also a Lenny system. I get this error when trying to mount.

*Thread moved to **Other OS/Distro Talk**.*

---

### Post by Drenriza on 2012-07-04
> **cortman said:**
> Are you even able to mount a device to /mnt? I always thought you needed to create a subdirectory in /mnt and mount it to there.

```
sudo mkdir /mnt/usb
sudo mount /dev/sdc1 /mnt/usb
```

/mnt is just a folder, so it's no trouble to mount a device to it.

> And it might be easier to help if you post the output of
```
sudo fdisk -lu /dev/sdc
```
I ran the command as root, but what output should i expect? Since i get **NO OUTPUT** at all.

---

### Post by sudodus on 2012-07-04
> **Drenriza said:**
> /mnt is just a folder, so it's no trouble to mount a device to it.


I ran the command as root, but what output should i expect? Since i get **NO OUTPUT** at all.

From your opening post:
> I have a device as such
 [6173721.285002] SCSI device sdc: 62734336 512-byte hdwr sectors (32120 MB)
 [6173721.285628] sdc: Write Protect is off
 [6173721.285663] sdc: Mode Sense: 23 00 00 00
 [6173721.285666] sdc: assuming drive cache: write through
 [6173721.285705] sdc: sdc1

If you have inserted your usb stick the same way as before, it should be recognized as sdc, and I would expect a list similar to the list for sda, sdb. Run ```
sudo fdisk -lu
``` to list all 'disk' devices.

---

### Post by Drenriza on 2012-07-04
Uhm yes i cant explain it. They unplugged the disk (external location) and plugged it back in (same physical port). And now i can mount the device to /mnt no trouble.

The output in my first post came from the dmesg command.

---

### Post by sudodus on 2012-07-04
> **Drenriza said:**
> Uhm yes i cant explain it. They unplugged the disk (external location) and plugged it back in (same physical port). And now i can mount the device to /mnt no trouble.
Guess: If you unmount a USB flash drive, you probably need to unplug and replug it in order to mount it again. Or it was some temporary error.

If you can repeat mounting after unplugging and replugging, I think it is OK :-)

---

