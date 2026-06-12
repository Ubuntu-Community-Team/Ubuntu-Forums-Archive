---
title: "dual boot with two SATA HDD none RAID"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by miqmaq on 2007-06-09
Hi forgive me if this is wrong place to post this query.
I am a complete novice so please bear with me, I picked up a copy of Ubuntu 7.04 Live CD, tried it liked it, my problem is I want to download updates to ubuntu which when I turn off PC are lost, so I would like to install onto hard disc, but I don't want to install onto my winXP hard drive, but would like to install onto other hard drive, ( I have 2 SATA hard drives none Raid on my PC ) and I would like to duel boot so that I can boot to either drive at startup, like I said earlier I am a complete novice so if you can point me in the right direction I would be very grateful.

Cheers

---

### Post by Moop on 2007-06-09
If you install Ubuntu to the spare hdd then it will detect XP on the other hdd and configure it to boot from grub. After Ubuntu is installed you will get an option to boot Ubuntu or XP. You shouldn't need to change any of the default boot options when you install Ubuntu but you probably will need to configure your bios to boot from the "new" hdd.

---

### Post by Liakath on 2007-06-09
> **Moop said:**
> If you install Ubuntu to the spare hdd then it will detect XP on the other hdd and configure it to boot from grub. After Ubuntu is installed you will get an option to boot Ubuntu or XP. You shouldn't need to change any of the default boot options when you install Ubuntu but you probably will need to configure your bios to boot from the "new" hdd.

Just to add: During Ubuntu installation you will have an option to install "GRUB" installer on the original (hda probably) or spare hdd (hdb / hdc / hdd depending upon how it is connected).

If you install on the original hdd (hda probably) the existing MBR of Windows will be modified and you will get the options to boot into WindowsXP or Ubuntu. In this case you can avoid the configuration of BIOS. You can continue it to boot from the original hdd (hda probably)

---

### Post by confused57 on 2007-06-09
> **miqmaq said:**
> Hi forgive me if this is wrong place to post this query.
I am a complete novice so please bear with me, I picked up a copy of Ubuntu 7.04 Live CD, tried it liked it, my problem is I want to download updates to ubuntu which when I turn off PC are lost, so I would like to install onto hard disc, but I don't want to install onto my winXP hard drive, but would like to install onto other hard drive, ( I have 2 SATA hard drives none Raid on my PC ) and I would like to duel boot so that I can boot to either drive at startup, like I said earlier I am a complete novice so if you can point me in the right direction I would be very grateful.

Cheers

This might be an option:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
the guide was written for IDE drives, but works with SATA also.

---

### Post by miqmaq on 2007-06-09
Hi
Thanks for quick response, but which option do I use on the installation page??, sounds dim I know, but there you go.

---

### Post by confused57 on 2007-06-09
> **miqmaq said:**
> Hi
Thanks for quick response, but which option do I use on the installation page??, sounds dim I know, but there you go.
See the section "Install Ubuntu Desktop CD" in this link:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Which option you choose will depend whether you're going to use the entire disk, or if you have data, you'll need to resize the current partition....you might want to read over the manual partitioning section.

---

### Post by miqmaq on 2007-06-09
Hi
I'm sorry but I thought it clear that I want to use one disk for WinXP and the other for Ubuntu, will one of the options give me a choice of which disk I use for XP or 7.04, also thinking about it, what if I had XP on both my hard disks, and I installed Ubuntu with the first option on the install page, would that give me DUAL boot??.
Cheers Mick

---

### Post by confused57 on 2007-06-09
> **miqmaq said:**
> Hi
I'm sorry but I thought it clear that I want to use one disk for WinXP and the other for Ubuntu, will one of the options give me a choice of which disk I use for XP or 7.04, also thinking about it, what if I had XP on both my hard disks, and I installed Ubuntu with the first option on the install page, would that give me DUAL boot??.
Cheers Mick
Sounds like your easiest option would be to use entire disk to install Ubuntu on...if it were my system, I'd enter bios setup, set your drive you're going to install Ubuntu on to boot before your XP drive.  When you get to the partitioning section, you'll see both drives listed & should see the XP NTFS partition on your XP drive...of course, select the other drive(probably /dev/sdb).  If you selected use entire disk, the installer will set up your partitions for you...you still might want to read over the "manual" partitioning steps in the link I gave you.  You might want to go ahead with the use entire disk, just to get experience with the Ubuntu installer and maybe later consider reinstalling using the "manual" partitioning option and set up a separate /home partition.
You'll be given an option to confirm your partition selections, before the your drive is partitioned...just make sure your XP partition isn't selected to be formatted, which it shouldn't be by default.


If you had XP on both hard drives and chose the first option, you'd select which disk & the installer would resize the XP partition by 1/2, then use the rest of the hard drive to install Ubuntu.

There's some excellent screenshots here of the installation process:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by miqmaq on 2007-06-14
Hi Confused

Sorry it took so long to answer your last post, but as you may have guessed I made a complete mess of install, in the end I messed up both discs, had to use third party software to reformat both of them, when they were nice and clean I took the plunge and installed Feisty.

Thanks for all your help, which I am too thick to follow:D but at least it gives me a chance, now that i'm commited to Ubuntu to go on and learn.

So thank to everyone that helped me.

Mick.

---

