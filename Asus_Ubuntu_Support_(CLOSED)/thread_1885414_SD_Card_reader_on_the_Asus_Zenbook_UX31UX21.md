---
title: "SD Card reader on the Asus Zenbook UX31/UX21"
date: 2011-11-23
forum: Asus Ubuntu Support (CLOSED)
---

### Post by erandom on 2011-11-23
Just wondering - have anybody tested the SD Card reader on the Asus Zenbook?
I haven't been able to get mine to work: A card is not detected at all (nothing appears on dmesg) when inserted.

According to the USB ID (0bda:0139), the device is made by Realtek. A device with similar id (0bda:0139) appears in [unusual_realtek.h]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=blob;f=drivers/usb/storage/unusual_realtek.h;h=e41f50c95ed409e7301ff5a8ad79334e16f08f2d;hb=HEAD") . However, making the kernel behave similarly with this device yields a failure to initialize the device during boot.

If somebody has any insight about the card reader, please share.

---

### Post by erandom on 2011-12-05
The solution, in form of a driver installation, can be found here:
[http://ubuntuforums.org/showpost.php?p=11062960&postcount=6](http://ubuntuforums.org/showpost.php?p=11062960&postcount=6)

---

