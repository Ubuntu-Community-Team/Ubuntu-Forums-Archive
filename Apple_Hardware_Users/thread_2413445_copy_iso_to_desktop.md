---
title: "copy iso to desktop"
date: 2019-02-25
forum: Apple Hardware Users
---

### Post by j3984 on 2019-02-25
Is it ok to drag an ISO to a folder on a mac and will it behave the same as the USB iso??that way the iso is available with out plugging in the USB drive..

---

### Post by wildmanne39 on 2019-02-25
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

---

### Post by Frogs Hair on 2019-02-25
> **j3984 said:**
> Is it ok to drag an ISO to a folder on a mac and will it behave the same as the USB iso??that way the iso is available with out plugging in the USB drive..

I believe it must be burned to disk or usb to boot though you should be able to view the files after download. Keep in mind on the desktop or file manager is on an already active partition. You can install in a VM also.

---

### Post by j3984 on 2019-02-25
i mean insert the usb  iso and copy the folder as a whole.

---

### Post by gsahli on 2019-02-26
If I understand what you mean - yes you can copy the ISO to desktop. But once it's there, you can't boot from it or install from it.

---

### Post by TheFu on 2019-02-26
> **j3984 said:**
> i mean insert the usb  iso and copy the folder as a whole.

no.  A bit-for-bit copy to a USB device is required if you want to boot from it. There are many tools to handle this - unetbootin, rufus, yumi, dd, ddrescue, but each will wipe any information on the flash drive.  The ISO has a boot sector in a specific location and that must be located in a specific location on the boot media/flash drive.

There are some multi-boot tools that do allow copying over specific ISO files to specific locations on a pre-setup flash drive. I've never used those.  Yesterday, I needed to make a flash drive that could be booted. Here's the exact command I used:
```
sudo ddrescue --force ./ubuntu-mate-16.04.5-desktop-amd64.iso /dev/sdb
```

Everything on sdb was completely wiped and replaced with the .iso file contents above.  If sdb isn't the correct target device, then bad things will happen, data loss is very likely.

---

### Post by ajgreeny on 2019-02-26
I am not sure how current the information in this thread is now, nor if it is appropriate for a Mac, but if you already have a Linux installed with grub2 (does a Mac use grub or something else when dual booting?) this may offer a method of booting directly to an iso file stored on its own partition on a machine.
[https://ubuntuforums.org/showthread.php?t=1838959](https://ubuntuforums.org/showthread.php?t=1838959)

Other Mac users may have much more info than I, a non Mac user have about this, so perhaps wait for more from them.

---

### Post by j3984 on 2019-02-26
got it

---

