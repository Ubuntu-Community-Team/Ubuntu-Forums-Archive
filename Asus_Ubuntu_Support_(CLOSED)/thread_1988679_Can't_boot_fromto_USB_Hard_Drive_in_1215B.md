---
title: "Can't boot from/to USB Hard Drive in 1215B"
date: 2012-05-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by belleberstinge on 2012-05-28
Okay, this is not specifically an Ubuntu problem, but so far this seems like the best place to get help for my problem.

I am unable to boot from, and boot to my USB HDD partitions. I have an Ubuntu installation on my internal HDD and another one on an external HDD. GRUB is installed into the MBRs and respective partitions of both drives.

[LIST]
[*]If I attempt to boot into the USB Ubuntu installation using the grub2 bootloader in the internal MBR and partition, my bootloader(?) is unable to detect the partitions on the external hard drive.
[*]If I attempt to boot from the USB HDD directly through the BIOS boot menu, I arrive at a blank screen.
[*]The USB HDD is able to boot when I use another computer.
[/LIST]

From these results, it seemed to me that the firmware has some problem with External HDDs at boot time.

[LIST]
[*]But quirkily enough, a USB flash drive with Unetbootin booting into an active FAT32 partition using Syslinux works. The flash drive becomes unbootable when I install grub2's MBR stage onto it.
[*]**edit:** I did some more testing and it seems that I was wrong when I said that grub2 does not boot from the flash drive. It does. So now I think the problem lies with an incompatibility with the USB HDD.
[/LIST]

So right now I do not know where the problem lies. Can someone suggest what I should try next to be able to boot to my USB HDD installation? Why does my BIOS refuse to boot to my USB HDD?

**edit2:** Okay, I solved the problem by using LILO. Not the most ideal solution, but I'm happy enough it now works. I'm thinking that the Ubuntu repo's grub2 bytecode hates my hardware configuration.

---

