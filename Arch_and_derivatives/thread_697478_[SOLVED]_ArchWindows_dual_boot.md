---
title: "[SOLVED] Arch/Windows dual boot"
date: 2008-02-15
forum: Arch and derivatives
---

### Post by bwtranch on 2008-02-15
Well, my son moved down here to Texas and is close now. He has a Pentium something (pretty new) with WindowsXP Pro. I want to do a dual boot with Arch and the Windows (gag) and since I'm not too keen on this (I hate dual boot systems), I was wondering if anybody has any advice. Particularily on the partitioning scheme. I like using fdisk and I think I know what to do, but without a working Linux distro on the thing, I'm not going to be very comfortable in that environment. Any thoughts would be appreciated.

---

### Post by Rumor on 2008-02-15
My approach would be to download either the gparted live cd [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/) or the parted magic live cd [http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php) and use it to set up your partitions. 

Boot the Arch install disc and set your file system mount points and proceed with the install as per usual. 

I've not used the parted magic disc, but I am familiar with gparted. It will allow you to shrink the Windows partition and then use the new space to set up your Arch partitions.

---

### Post by bwtranch on 2008-02-15
Thanks. We'll see how that goes. I am going over and bring the machine here today.

---

### Post by santaslittlehelper on 2008-02-15
I would go with gparted as well. 

Just to add, I don't know how important this is but I think it's recommended to defrag before resizing a windows partition.
As for partition scheme I would make sure to do an extended partition for arch and any other partitions that might be needed.

Good luck.

---

### Post by manmower on 2008-02-15
My current setup is the main Windows XP NTFS partition holding the operating system and installed programs, followed by an extended partition which holds everything GNU/Linux-specific: swap space and an Ext3 root partition for Arch (followed by the same for Ubuntu, but this is less relevant to you). Unless you're going to install a BSD or something in the future, you are safe making these all logical partitions. The rest of my disk is a big primary NTFS partition that holds all my data. I find GNU/Linux's support for NTFS through NTFS-3G to be better than Windows with Ext2IFS or whatever. Just enter the correct options & locale in fstab and it will never give you worries.Also, and again this is probably less relevant to you, I keep my data partition synced with a directory on another Windows machine in our home network. Having it as NTFS on my own machine eliminates any possible ugly issues with conversion of weird characters in folders and filenames rendering them useless and such.

---

### Post by bwtranch on 2008-02-15
Thanks santa and manmower. Manmower that is really good advice and I think I'll read it again, it was so good!
But, you know. after thinking about it. I think I'm gonna try Ubuntu with him. Hey, wait, I may be back.....:)

---

