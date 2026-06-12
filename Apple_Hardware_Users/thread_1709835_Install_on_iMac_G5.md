---
title: "Install on iMac G5"
date: 2011-03-18
forum: Apple Hardware Users
---

### Post by Saeros on 2011-03-18
Hey there,

Installed ubuntu on my imac g5 pre isight.  Completed with no problems.  Then decided on using a 2TB hard drive instead of the 250GB drive that came with the iMac.

So I swapped out the hard drive, and proceded with the install.  Had some trouble getting the hard drive to recognize in ubuntu. had to set the jumper so that it'll use the legacy SATA interface.  FINALLY had it recognized and then installed ubuntu with what seemed to be no issues.

When that was all good, it rebooted and displayed the folder with question mark in it.  I rebooted the mac a bunch, and finally it booted into the First Stage bootstrap.  I then pressed enter, and it went to yaboot.

After that, everything goes to hell.

I press enter again, it selects Linux
This is what displays:
```
Please wait, loading kernel...
    Elf64 kernel loaded...
Loading ramdisk...
malloc failed
/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:3,/boot/initrd.img: Unknown or corrupt filesystem
ramdisk load failed !

Apple PowerMac8,2 5.2.5f1 BootROM built on 04/06/05 at 12:46:02
Copyright 1994-2005 Apple Computer, Inc.
All Rights Reserved.

Welcome to Open Firmware, the system time and date is: 03/19/2011 01:53:43 

To continue booting, type "mac-boot" and press return
To shut down, type "shut-down" and press return
Reducing system power...

  ok
```

Is this because I'm using a 2TB hard drive? I've heard of issues surrounding them potentially.... especially because of the larger block size that's required.  How can I make sure that that's happening?

I was also thinking of manually choosing the file system, but am unsure of what i should select.

Thanks for any help you can provide.

---

### Post by juanix on 2012-03-30
Hi Saeros,

I have the exact same problem with a PowerMac G5 (Tower). I also have a 2To byte hardrive. I will try to install it on a smaller drive to see if it's the real problem.

I'll keep you inform.

---

