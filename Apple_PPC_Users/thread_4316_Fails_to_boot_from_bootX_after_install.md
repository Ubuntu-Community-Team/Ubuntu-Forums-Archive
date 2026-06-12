---
title: "Fails to boot from bootX after install"
date: 2004-11-13
forum: Apple PPC Users
---

### Post by heavyt on 2004-11-13
I was able to install ubuntu on an oldworld mac (powercurve with g-3 chip) but it will not boot into the new installation with bootX! I have used bootX before with Debian  and Yellow Dog so I feel that there is something gone wrong with the installation process that we do not have any control of, but maybe there is a work around for it.  :?

---

### Post by Tommy on 2004-12-04
[QUOTE=heavyt]I was able to install ubuntu on an oldworld mac (powercurve with g-3 chip) but it will not boot into the new installation with bootX! I have used bootX before with Debian  and Yellow Dog so I feel that there is something gone wrong with the installation process that we do not have any control of, but maybe there is a work around for it.  :?[/QUOTE]

From your experience with the other linuxes you already know that you have to manually switch from the installer's initrd and make some other changes when it boots. Actually the HARDEST part is copying the new kernel from the ext3 partition to the Mac partition that you're going to boot from. You can't do it directly because the installer doesn't have HFS (Mac Filesystem) drivers.

I have personally not yet successfully installed Ubuntu on my oldworlds but I have gotten far enough that I think the biggest problem is the stock kernel may not have the drivers it needs for the particular Macs I was trying on. For example I have an ATA card in one, but the kernel does not have that module compiled in, so I would need to find or compile one that does.

The powercurve might have some other wrinkles, too, but they would be similar to whatever you did to get Debian and Yellow Dog going.

You might try a Debian 2.6.x kernel to see if it can boot Ubuntu. (I don't know of a reason it would not work but I am not an expert!)

---

### Post by monkeyshaman on 2004-12-04
I've got Ubuntu installed on my 1998 Powerbook G3 and it boots, but only goes as far as loading the linux partition.  Then it stops and say it can't load the partition and I need to use additional "root=" boot options in order to get it to work.  I'm using BootX and the partition is /dev/hda7 (the Mac OS is on hda8 and the swap partition is hda9).  Anyone got a clue what options I need to use?

Thanks...

Arnold


UPDATE!!!!
I figured out how to do it.  I renamed the initrd file from the long name (initrd.img-something-something-something-powerpc) to just initrd.img and then I moved it to the root of the Mac OS partition.  After that, it booted and ran like a champ! :)

---

### Post by Tommy on 2004-12-05
[QUOTE=monkeyshaman]I've got Ubuntu installed on my 1998 Powerbook G3 and it boots, ...

... renamed the initrd file from the long name (initrd.img-something-something-something-powerpc) to just initrd.img and then I moved it to the root of the Mac OS partition.  After that, it booted and ran like a champ! :)[/QUOTE]

Great! I use Debian on this 1998 PowerBook G3 Series ("PDQ") and eventually I will try Ubuntu on it. I gather you were successful using the stock kernel. 

The original poster in this thread uses a PowerCenter and an ATA card, which is similar to the PowerMac 9600 with an ATA card I worked pretty hard to make it work. I was mostly successful getting it to boot Debian but not at all successfull with Ubuntu. I'm almost certain a different kernel would boot it just great. It may require a custom kernel.

The only thing that kept Debian from being *completely* successful on that machine is that when using the ext3 file system, the data corrupts itself either during install or after a few minutes. Based on other systems and some experiments I have decided it's an ATA issue. Better hard drive cables (80-wire ones) have helped but not completely resolved it. I have been more successful with ext2, but since the only difference between the two is journaling, there's not an easy explanation.

---

