---
title: "Problems trying to install Win on Asus F501A with Ubuntu 13.04"
date: 2014-02-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by kuro2 on 2014-02-01
Hello!

I have a little problem with my PC. I have an ASUS F501A ([http://xtremmedia.com/Asus_F501A_XX353H_i3_2370M_4GB_500GB_15_6.html](http://xtremmedia.com/Asus_F501A_XX353H_i3_2370M_4GB_500GB_15_6.html)) with Win8 preinstalled. When I made a partition to install Ubuntu, the program crashed while doing it. The result just was that I had my HDD formatted and I installed Ubuntu normally so I could install Windows after that.

So, now I have my PC with Ubuntu but I want to have a Dual Boot with Win7/8. My computer cannot read CD/DVD, so I tried to install it from a USB. Here's the problem.

I tried with all kind of different Windows images, with different pendrives and mounted the iso with many different programs and I cannot launch it properly. I think my problem is that I have UEFI, but I followed many tutorials to prepare the USB for UEFI but they didn't work.

I'm really desperated with this and I hope you could help me out D:

---

### Post by PrSdNt on 2014-02-05
Use unetbootin (available from the repository).

1. sudo apt-get unetbootin
2. start gparted and delete all partitions from the USB, then create a single fat32 partition
3. After the partition is created, mount it again .
4. Start unetbootin, select the .iso and USB drive en click start.

I also have a very recent ASUS mobo and it works great.

Also make sure you use a 64-bit version of ubuntu

---

