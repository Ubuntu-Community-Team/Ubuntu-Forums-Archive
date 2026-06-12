---
title: "booting ubuntu from iso on HD"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by kadee on 2007-11-03
Hi,

I'd like to boot ubuntu-7.10-desktop-i386.iso from HD image which I've already tested booting the burnt image from a CD. I've configured the /grub/menu.lst, but for some reason the images of "linux" and "initrd.gz" that I've downloaded boot me into an installation walk-through. This would be fine if I wanted to proceed with the install. I've poked through the .iso file to see if I could locate the two files, but for some reason could not find them. Unless of course I did something wrong. When I boot kanotix or the new thorhammer in this way, in addition to initrd.gz the other file is vmlinuz. Is there another kernel image that I should be using instead?

here's the menu.lst
--------------------------
title UBUNTU
    kernel (hd0,2)/ubuntu/vmlinuz ramdisk_size=14972 root=/dev/rd/0 rw --
    initrd (hd0,2)/ubuntu/initrd.gz

I did finally locate the initrd.gz and vmlinuz images in the casper folder. However, when booting the system hangs and generates following error:
"ALERT! /dev/rd/0 does not exist. Dropping to a shell"

Regards,

kadee

---

