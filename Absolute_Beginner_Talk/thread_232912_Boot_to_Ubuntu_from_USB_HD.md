---
title: "Boot to Ubuntu from USB HD"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-08-09
Hi
I'm trying to set up a system where I can boot from a USB HD to Ubuntu by means of a Boot CD and I'm following the instructions given here:

> [http://zerlinna.blogweb.de/archives/52-Dual-boot-on-external-USB-Drive-with-a-BootCD-with-Bios-not-supporting-boot-from-external-device.html](http://zerlinna.blogweb.de/archives/52-Dual-boot-on-external-USB-Drive-with-a-BootCD-with-Bios-not-supporting-boot-from-external-device.html)


Two points are important here:
1. I already have a more recent version of Ubuntu (6.06) installed and operational on my internal HD
2. My computer's BIOS does not recognize the USB HDs as bootable.

However, the boot using the boot cd fails due to inability to recognize the designation of the partition (on the usb hd) where the NEW Ubuntu system (5.10) is installed.
Operating from Ubuntu 6.06 (internal HD), the NEW Ubuntu is installed on a partition with device name /dev/sda9 and mount point /media/usbdisk-3.

The isolinux.cfg file, which is included in the bootcd iso, therefore consists of the  following line:

```
DEFAULT linux initrd=initrd.img ro root=/dev/sda9
```

However, on boot up from the bootcd, an Alert is displayed saying that /dev/sda9 does not exist.

Yet, when I reboot to Ubuntu 6.06 (internal HD), and run df -h, this partition is clearly indicated as I specified above.

I would be grateful for any suggestions as to how I can rectify matters.

Thanks 
Paul

---

