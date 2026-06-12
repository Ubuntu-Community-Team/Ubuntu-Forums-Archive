---
title: "How to boot an USB stick  with Ubuntu (live or installed) on a macbook"
date: 2011-06-29
forum: Apple Hardware Users
---

### Post by dodino on 2011-06-29
Hi all,

I'm aware that this topic has been discussed several times, but after reading a lot of posts about it and followed many howto without success, I hope to find an updated solution to solve my problem, writing a new post.

I have a macbook black (2008 edition) and I want to boot an Ubuntu installed on my USB stick (Corsair Voyager GT 16GB) on my Macbook.

Reading online seems to be possibile but not easly, anyone have a good howto that explains in detail and, above all, correctly? All howto that I have followed don't work, during the boot returns the error "Missing operating system" or similar.

I guess the problem is due to the "structure" of the USB flash drive, ie the partition table and the bootloader, but I not understand well what might be the right combination, for example GPT with EFI partition, or an MBR partition table with a primary FAT partition that must have the bootloader installed into it (grub for example), or other type of configurations...

Of course I installed rEFIt on my macbook, so I can read the USB device at startup, but not is enough to boot the USB drive, I must configure it in a particular way, which until now have not managed to do.

After many days of readings and tests, I sincerely hope that someone knows the solution to help me.

Thanks,

Edoardo T.

---

