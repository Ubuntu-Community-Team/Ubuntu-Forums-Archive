---
title: "Xubuntu on Power Mac 8600...Hmmm...."
date: 2006-11-28
forum: Apple PPC Users
---

### Post by spodie on 2006-11-28
All right. After chasing my tail for two weeks trying to install either NetBSD, Debian, or Gentoo on this aging Power Mac 8600, I finally gave in and decided to install Xubuntu Edgy, due to this machine being Old World, and more because Xubuntu doesn't have very steep system requirements. My two weeks with the aforementioned distros were a living hell, compiling kernels and futzing around with Open Firmware, which I actually know how to do.

I downloaded Edgy, burned it to CD, and remembered that the CD drive in this oldster won't mount anything larger than 650 MB. I drove all over town searching for 650 MB blanks or rewritables, until I finally found an old, unopened, 5-pack of 650 MB CD-RW discs collecting dust on a back shelf at Office Depot. I was more than happy to take them off their hands. I burned the RW, configured BootX, and booted into Edgy's installer. What a sight for sore eyes!

Before I proceed with my problem, here's a little info on the 8600: 320 MB RAM, 4 MB VRAM, IMS TwinTurbo 3di, SCSI CD-ROM, 4 GB SCSI hard drive on native bus, and 9 GB U2W hard drive connected to Initio Miles U2W PCI SCSI card. In all the previous attempts at installing Linux on this machine, none would recognize the U2W drive or card for use at all. I decided to dedicate the 9 GB drive to Mac OS 9, and the 4 GB drive solely to Linux, which is the exact opposite of what I intended. No matter. I was hell-bent on getting Linux installed on this 8600! We'll not even discuss the TT3di!

After much hemming and hawing, I was finally able to get Edgy installed on the 4 GB drive with no problems. The installer ran perfectly. At the end of the installation, it told me that the /vmlinux Kernel was on /dev/sda2, and the Root was on /dev/sda3. I took note of these locations and rebooted. I reopened BootX, turned off the ramdisk image, and changed the Root Device to /dev/sda3. I turned off all the other settings, including Force SCSI On and Force Video Settings. I saved the preferences, and clicked the Linux button.

The boot sequence comes up, and abruptly ends, saying "Rebooting in 180 Seconds." A little further up the list, it tells me that it "Cannot open root device "sda3" or unknown-block (0.0)" I have changed the Root Device to every partition I can think of, and come up with the same results. I have tried different kernel arguments without success. At least the system is installed. That's further than I've ever gotten with any other distro.

Here while back I read something on the Ubuntu Wiki about pointing the Linux install to the Mac install so they can communicate about booting between them. This would not be a problem, but the OS 9 install is on the U2W drive on the Miles U2W card, which is not recognized by Linux at all.

What do I need to do? Anyone have a better suggestion than using a second narrow SCSI drive on the same bus as the first for OS 9? I'd sure like to use the U2W drive with Linux, with it being so much faster than narrow SCSI. But alas, I probably have no choice!

Any suggestions humbly appreciated. Thanks kindly.

---

### Post by Brian Smith on 2006-11-28
You didn't specifically say, but probably you did copy the newly installed Linux kernal from your Ubuntu hard drive onto your Mac OS hard drive partition containing BootX, is that right?  Try deleting the BootX Linux Kernal and ramdisk image from the Mac OS partition, and use solely the new kernal and ramdisk image, so that your new kernal and ramdisk image are the only ones BootX can find.  
I don't know if you MUST only use the new kernal and matching ramdisk image (renamed as specified by BootX instructions!) but I DO know that doing so gave me success when I was having similar troubles.

---

