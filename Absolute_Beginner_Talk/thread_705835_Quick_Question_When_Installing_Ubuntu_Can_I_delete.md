---
title: "Quick Question: When Installing Ubuntu Can I delete all previous partitions?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by biffinson on 2008-02-23
When Installing Ubuntu Can I delete all previous partitions?

I'm setting up a dual booting laptop with xp/ubuntu, and was going to install xp first ( as i know with the  xp setup you can delete all partitions, make new ones and etc) but are you able to do so on linux as well?

Basically, I want to delete all partitions on my hard drive, make one for ubuntu, install it on that partition, then go back with xp later and install it on the other partition

Is this possible using the ubuntu setup?

Thanks!

---

### Post by JoshuaRL on 2008-02-23
Yes you can, and the option in the installer is "Guided - Use entire drive".

But it's much harder to install XP, or any Windows OS, over an existing Ubuntu OS.  The reason is that Windows is kind of greedy and thinks it should be the only OS on the drive.  In so doing, it overwrites the entire MBR, including GRUB, and so can be tricky.

Your Ubuntu partition will still be there, but you'll need to reinstall GRUB and make sure it's configured correctly to do it that way.  Much easier to install XP first, then let Ubuntu install after using "Guided - Partitioned".

---

### Post by hypocratus on 2008-02-23
It is best to install XP first, otherwise it's boot manager will overwrite the Ubuntu's GRUB. But you can make partitions using the partition tool in the installation just like in XP. You can even use the boot manager that XP has instead of GRUB. It just takes more work.

---

### Post by Rocket2DMn on 2008-02-23
Yeah, of course.  When you go to install (from whichever OS you do first), just leave enough space Unpartitioned for the other OS.  We suggest doing XP first, then installing Ubuntu so you don't have to go through the hassle of reinstalling GRUB.
That is to say, if you install XP second, you won't get the option to boot into Ubuntu because XP will take over the bootloader, but you need GRUB to access Ubuntu.  However, if you DO attempt this, you can reinstall GRUB by this guide: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by cboebel on 2008-02-23
I have had a great deal of success installing ubuntu first, and then installing Windows XP as a virtual machine using VMWare. The advantages are that you can run XP and Ubuntu simultaneously, and share files between them. This has worked out for me because I would like to do most of my work in linux, but have found that I still like to use some tools (photoshop, indesign) in XP.

---

### Post by sandysandy on 2008-02-23
> **biffinson said:**
> When Installing Ubuntu Can I delete all previous partitions?

I'm setting up a dual booting laptop with xp/ubuntu, and was going to install xp first ( as i know with the  xp setup you can delete all partitions, make new ones and etc) but are you able to do so on linux as well?

Basically, I want to delete all partitions on my hard drive, make one for ubuntu, install it on that partition, then go back with xp later and install it on the other partition

Is this possible using the ubuntu setup?

Thanks!

as others have mentioned it is better to have XP install first and then do ubuntu. however even if u do an XP install later u can still reover the MBR but that would take some effort.

on the other issue of hard disk partitioning, if u are very sure of how many partitions u want, i would suggest that you partition your hdd before doing installation to avoid any confusion whatsoever later on. one good utility for partitioning is GParted which u can download from net (google it) and then burn ISO image to have bootable gparted CD.U can then partition ur hdd as desired. remember u can have at most 4 primary partitions. one of these primary partitions can be an extended partition in which u can have further partitions.

the partitions can be formatted as NTFS for windows and Ext3 for Linux. 

when installing XP do so in NTFS partition. Linux should be installed in ext3 partition. linux will also require Swap, which u can let the linux installer create (or make beforehand using gparted )

regards

---

