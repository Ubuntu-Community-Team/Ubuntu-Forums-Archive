---
title: "USB 7.10 Live with persistance"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by MotF Bane on 2007-11-22
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

I followed every line of those directions, with the exception of adding "http://" for step 19.  However, it still will not work, and my motherboard's POST screen informs me of a boot error.  I've booted using that same USB key (after setting it up in Windows) to flash ATi video card BIOS, so I don't *think* that it is the motherboard or USB key.  Is there a way to concretely identify what component is not working, or is there something essentially wrong within that guide?  

If it helps...
USB key - Sandisk Cruzer Titanium U3 1GB (U3 has been deleted)
Ubuntu 7.10 Live CD
DFI P35-T2RL Blood Iron motherboard

Also, if it helps, I tried doing something similar with Fedora 8 last night, although without a concrete guide, but it didn't even acknowledge at all.

---

### Post by bumanie on 2007-11-22
I have been successful booting both a external hdd and usb pen with puppy linux (have not tried full size distro). Check out this link, it should work. Note you need an iso image of the distro rather than a cd image.
[http://www.pendrivelinux.com/2007/03/09/use-qemu-to-boot-linux-from-windows/](http://www.pendrivelinux.com/2007/03/09/use-qemu-to-boot-linux-from-windows/)

---

### Post by Phurious on 2007-11-22
Did you try:

```
lilo -M /dev/sdx
```

I had the same problem, but his cleared it up.

---

