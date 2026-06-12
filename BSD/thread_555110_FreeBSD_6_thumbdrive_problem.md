---
title: "FreeBSD 6 thumbdrive problem"
date: 2007-09-19
forum: BSD
---

### Post by theonlyrealperson on 2007-09-19
I have a little problem with my FreeBSD stable and my Creative Zen Nano device. When I had my FreeBSD Release version, it worked fine, but now it doesn't create a dev device when I plug it in. dmesg tells me that it recognizes Creative Zen Nano, and no error messages...

Usbdevs also recognizes it as a Creative Zen Nano. But, still no da0s1 or sd0... I have all the proper usb devices loaded into the kernel as listed in the FreeBSD handbook. I also am loading HAL, dbus, polkit, etc. in my rc.conf...

Anyone have any ideas?

---

### Post by Bachstelze on 2007-09-20
Could you please paste the exact dmesg messages ?

---

### Post by theonlyrealperson on 2007-09-20
Sorry it took me so long. Here is the dmesg:

```
umass0: CREATIVE Zen Nano Plus, rev 2.00/11.11, addr 6
xptioctl: pass driver is not in the kernel
xptioctl: put "device pass0" in your kernel config file

```

"pass" is in my kernel, but not "pass0". I've never heard of the device pass0. I know I didn't have it in my 6.2 Release kernel, and it worked. Anyway, weirder yet, it didn't say that last night when I plugged it in!!!!

When I plugged it in a second time, it no longer says it, it just says:

```
 umass0: CREATIVE Zen Nano Plus, rev 2.00/11.11, addr 6
```

the command "usbdevs" hung the first time I plugged it in. And then the second time it says:

```
addr 1: UHCI root hub, Intel
addr 1: UHCI root hub, Intel
addr 1: UHCI root hub, Intel
addr 1: EHCI root hub, Intel
 addr 2: product 0x1521, vendor 0x04cc
  addr 6: Zen Nano Plus, CREATIVE
  addr 3: product 0x1001, vendor 0x047e
  addr 4: Targus Group Intl, Targus Group Intl
  addr 5: USB PS/2 Keyboard - PS/2 Mouse, MCT
```

What do you think?

---

### Post by Bachstelze on 2007-09-21
Well, usually when you plug in a USB drive, it says something like

```
umass0: USB Solid state disk, rev 1.10/1.00, addr 2
GEOM: create disk da0 dp=0xc2d74850
da0 at umass-sim0 bus 0 target 0 lun 0
da0: <Generic Traveling Disk 1.11> Removable Direct Access SCSI-2 device
da0: 1.000MB/s transfers
da0: 126MB (258048 512 byte sectors: 64H 32S/T 126C)
```

Have a read at [this](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/usb-disks.html) and make sure you have all the listed drivers in your kernel. Also, try adding "pass0", never hurts to try what the OS suggests :D It's been a while since I used FBSD, maybe womething changed in STABLE.

---

### Post by theonlyrealperson on 2007-09-21
> **HymnToLife said:**
> Have a read at [this](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/usb-disks.html) and make sure you have all the listed drivers in your kernel. Also, try adding "pass0", never hurts to try what the OS suggests :D It's been a while since I used FBSD, maybe womething changed in STABLE.

Yeah, that's the first place I looked. (On the side, what fantastic documentation FreeBSD has. I can't say enough good things about it.) 

I've noticed some changes between STABLE and RELEASE, so maybe you're right. I'll re-roll my kernel and add pass0 and see if it works.

Every other external USB drive I have works, doesn't matter the file system - just not my Creative Zen Nano... That's just weird. :confused:

---

