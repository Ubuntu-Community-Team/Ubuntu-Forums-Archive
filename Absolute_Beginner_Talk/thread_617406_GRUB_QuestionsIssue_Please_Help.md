---
title: "GRUB Questions/Issue Please Help"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Orius on 2007-11-19
Hello,
Recently installed Ubuntu 7.10 to my external usb hard drive along with GRUB. Windows XP Pro is installed on my internal hard disk. The issue/problem I am running into is that I get a GRUB error when booting the computer with the USB drive uplugged/turned off. GRUB gives Error 21 (Selected disk does not exist) which makes sense since the drive is off/not plugged. I cannot go any further after receiving the error.
My questions:
1) Is there no way to by pass this error and boot windows? Or is a "bypass/workaround" not possible because GRUB is installed on the unplugged/"missing" HD?
2) Would installing a GRUB partition on my internal HD (will always be there) allow me to by pass the grub error? How do I remove GRUB from Ubuntu on the external HD so that it will not conflict with the GRUB partition.
3) When I boot the computer with the USB HD unplugged/off where does the first part of GRUB boot from? Is there a portion of GRUB installed on the Internal HD (windows)? When looking at the windows drive I see no files or folders having to do with GRUB, so are the GRUB components stored in the MBR?

I have read over most of "[The GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm#21")" but have not found a good answer to my questions.

Thanks,
Zack

---

### Post by mikewhatever on 2007-11-19
There are two ways (could be more :-)) to tackle your problem. One, creating a separate boot partition [http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)
I could not possible explain it better then Herman, so check it out.

Two, using two boot loaders, one for Windows and one for Ubuntu. If your computer is capable of booting from USB, you could set that option before HDD, so if the external HDD is plugged in, it would load grub and boot into Ubuntu, otherwise, the second option would be used to boot from the internal HDD and load XP with its own native bootloader.

---

