---
title: "ZFS on a root filesystem and Apple hardware"
date: 2013-09-17
forum: Apple Hardware Users
---

### Post by horizonbrave on 2013-09-17
Hi all,
thanks in advance for patience from a gnu/linux novice =)


It's been many years since I tested a linux debian distro and I decided than now I'm ready and that I don't wanna delay the installation any longer.
To keep things initially easier I thought about Ubuntu, to make them definitely harder I'll let you know I'm on Apple hardware (an Intel MacBook Pro 64bit) and to make things even more complicate I absolutely want to install on a ZFS "partition". I just started to study ZFS but not having a strong IT background many questions (most will sound silly to you, be ready) come to mind and I hope you can help me a little bit to make things clear.


1) In order to install gnu/linux on a ZFS root filesystem ([https://github.com/zfsonlinux/pkg-zfs/wiki/HOWTO-install-Ubuntu-to-a-Native-ZFS-Root-Filesystem](https://github.com/zfsonlinux/pkg-zfs/wiki/HOWTO-install-Ubuntu-to-a-Native-ZFS-Root-Filesystem)) do I need to dedicate the entire disk to ZFS or I can split in 2 "partitions" in order to be able to boot in Mac Os X as well (FYI it's a SSD disk)? for some reasons I wonder if ZFS requires me to give it control of the entire disk...


2) Knowing this eventual dual boot set up will give me some initial installation problems do you think that installing another hard drive in the laptop (in place of the DVD burner) and dedicating one disk to each OS will give me some real advantage?


3) If I understood well with ZFS there are no partitions: what about the assumption that for security reason usually the /boot and /home should better have dedicated partitions? am I gonna loose a bit of security or not really?


4) I saw that the zfsonlinux.org link to debian just point to an installable package and I presume that way it only gives the os a zfs compatiblity: will in this case (or with any other distro) be able to upgrade to a full root ZFS filesystem in a second time without too much hassle?


5) I thought about going the OpenIndiana way but I somehow have the feeling that I will enjoy more learning/studying linux rather than a BSD style system and I think that for a desktop station it would be much better and versatile to stick with linux.


Thanks for helping me in these my first steps into the penguin world

---

### Post by horizonbrave on 2013-09-17
Hi all =)
and sorry for cross posting.

I'm want to install Ubuntu on ZFS root filesystem.
I just posted a thread about it here: [http://ubuntuforums.org/showthread.php?t=2174957](http://ubuntuforums.org/showthread.php?t=2174957)

Just wanted to let you know since it's on a MacBook Pro and some of the questions are strictly Apple related.
Please answer that thread if you feel keen in giving any help/contribution.

Thanks a lot

---

### Post by tgalati4 on 2013-09-17
List all of the reasons that you want to use ZFS on a linux system.

ZFS works best on a BSD system, so unless you plan on running a BSD derivative, you might experience some issues with linux.  I would stick with Ext4 for Linux on a mac.  You want to reduce the agony units.  If you do have an issue with your system, you have confounded the situation because you will never know if the problems are from zfs or from running Linux on Mac hardware.

If you want to learn ZFS, then install with a BSD derivative on Intel/x86 hardware (not Mac).  If you just want Linux on your Mac, then load a plain, vanilla linux distro that others are using on Mac hardware.

---

### Post by coffeecat on 2013-09-17
Threads merged.

---

