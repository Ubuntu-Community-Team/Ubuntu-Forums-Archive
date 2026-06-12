---
title: "Booting unbuntu from external drive"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by amoroso3645 on 2007-06-27
ok so i have unbuntu loaded on an usb connected external drive. When i plug it into my WinXP laptop and select it to boot up from the usb it will not work. I'd like to be able to boot it without altering much on my laptop. When I first installed ubuntu on the external drive thru my laptop, I messed up my laptops MBR so that I needed to have the external drive plugged in just to boot up XP. Now that I fixed that I cannot boot up ubuntu when it is plugged in.... any ideas???

---

### Post by Pragmatist on 2007-06-27
Have you configured your BIOS to boot from the USB drive?

---

### Post by confused57 on 2007-06-27
> **amoroso3645 said:**
> ok so i have unbuntu loaded on an usb connected external drive. When i plug it into my WinXP laptop and select it to boot up from the usb it will not work. I'd like to be able to boot it without altering much on my laptop. When I first installed ubuntu on the external drive thru my laptop, I messed up my laptops MBR so that I needed to have the external drive plugged in just to boot up XP. Now that I fixed that I cannot boot up ubuntu when it is plugged in.... any ideas???

You need to install grub to the external drive's mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

```
sudo grub
find /boot/grub/stage1
root (hd1,x)
setup (hd1)
quit
```
read the howto, but it will be something like the above

Then you should get a grub boot menu when you boot first to the external drive, highlight the Ubuntu entry, press "e", change root from (hd1,x) to (hd0,x), then press "b" to boot...this is temporary, but can be made permanent if it works.

---

