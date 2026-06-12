---
title: "Damn Small Linux - rip ISO to a partition and having grub see it to boot from it"
date: 2011-06-12
forum: Any Other OS
---

### Post by slooksterpsv on 2011-06-12
All,

I'm trying to figure out how to do this, and it's proving to be a pain, unless you have another HDD or burnable cd.
Here's the gist of it:

My friend downloaded and burned DSL to a disc, thinking it would support flash, videos, etc. but it doesn't due to the kernel being so old (2.4.xx). So we downloaded Xubuntu Natty ISO, but he doesn't have a blank CD to burn it to.

So I figured, why don't we partition the drive, rip the ISO to an unformatted partition, update grub to allow booting from it, and boot into Xubuntu install, and go from there.

Anyone have any ideas how to do that? I know we'd do:
dd if=iso_file of=/dev/hda2 (for the partition)

I just don't know how to update grub to allow booting directly from the /dev/hda2 partition. (The reason HDA2 and not HDA or HDA1 is cause the ISO is on HDA1).

Tricky isn't it?

---

### Post by tgalati4 on 2011-06-13
[http://slitaz.org](http://slitaz.org)  Lightweight and has chrome 13 unstable.

I don't think grub can boot off of a specified hard disk partition without finding the initrd (initial ram disk) and the kernel.

For example:

title		Linux Mint 7 Gloria, kernel 2.6.28.10-slim
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.28.10-slim root=/dev/sda2 ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.28.10-slim

But supergrub or plop bootloader might do the trick.

But give slitaz a spin.  With google chrome, you can watch a lot of stuff with html5 goodness.

---

### Post by slooksterpsv on 2011-06-13
> **tgalati4 said:**
> [http://slitaz.org](http://slitaz.org)  Lightweight and has chrome 13 unstable.
Not gonna help I need a flash drive or a burnable cd or another computer to do that. My friend doesn't have any of those.

> 
I don't think grub can boot off of a specified hard disk partition without finding the initrd (initial ram disk) and the kernel.

Yeah maybe... but then how does it boot off of Windows via chainloader? I was thinking it could do that.

> 
...
But supergrub or plop bootloader might do the trick.


Yeah well the DSL kernel is 2.4.31 it's old and trying to run anything has tons of missing dependencies and a compile is not an option.

> 
But give slitaz a spin.  With google chrome, you can watch a lot of stuff with html5 goodness.

See above.

---

### Post by tgalati4 on 2011-06-15
I don't know if Grub's chainloader +1 can boot off of an ISO image.  Perhaps there are other switches besides +1.  Newer machines can sometimes bring up a boot menu.  F12 on my thinkpad will scan and bring up valid boot devices, so if a partition contains a bootable ISO image and the BIOS scans it, then you can select it to boot from.

For copying the image, you would have to research the appropriate dd parameters.  I'm lazy, I would try the following:

Make an 800 MB partition (preferable on the back end of a non-critical drive).

sudo cp /dev/cdrom /dev/sda4

Make sure you call out the correct partition as it will overwrite indiscriminately.

Then either try the chainloader in grub or look into BIOS boot options.

---

