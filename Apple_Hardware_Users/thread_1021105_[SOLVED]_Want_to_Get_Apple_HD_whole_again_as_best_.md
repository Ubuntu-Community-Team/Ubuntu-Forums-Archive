---
title: "[SOLVED] Want to Get Apple HD whole again as best I can"
date: 2008-12-25
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-12-25
Hi,
  I'm on a Mac Mini and I'm giving it to my Dad as a Christmas gift, and while it's virtually new and hasn't been used, I did install Ubuntu on it with a dual boot through rEFIt.

I just now did a whole erase-install of Leopard with the original disk, thinking this would erase the Linux partition. But in checking Disk Utility, I see the linux partition is still there.

I know there's no easy answer here and that trying to restore a Mac HD to wholeness is almost impossible. What are my options here?

Many Thanks, Frank B.

PS I don't think my Dad would go for using Ubuntu, so I'd like to not entertain the option of keeping it on.

---

### Post by xstriker on 2008-12-25
I just did this same thing, and to do it I downloaded and burned an iso of gparted. I booted up and simply deleted ALL the paritions on the drive, the 3 linux I had (boot, main parition and swap) as well as the HFS+ one for leopard, leaving ONLY the efi bootspace that was 200 mb. I wrote those changes, popped in leopard and installed away which just let leopard use all the available hard disk.  

you could probably do the same thing with the ubuntu live cd!

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by hajk on 2008-12-25
Well, you could always remove those Linux partitions in Disk Utility, and then use the diskutil program in a Terminal to expand the Macintosh HD to fill up the whole drive, read the man-page for diskutil for the details -- but this is a dicey undertaking. Safer is to use your Ubuntu liveCD and then start the gParted partition manager (in the System - Administration menu) to completely delete all partitions on the drive (don't forget to Apply), and then logout from the liveCD and reinstall Leopard from scratch.

---

### Post by Brightbelt on 2008-12-25
Thanks Guys! G-Parted did the trick (I used an Ubuntu LiveCD), although the Linux Swap partition was greyed out and it wouldn't let me delete it. But that's just a very small bit of space, so it's not so crucial. 

When I put Leopard in, it got to the part where you pick your drive to install it, and there was a blank area (no hard drive to choose) because I had deleted all partitions, so there was a menu up top with Disk Utility on it, so that's where I went to repartition the drive. Just thought I'd mention this because it could trip some folks up.

Many Thanks!
Frank B.

---

### Post by cyberdork33 on 2008-12-28
really all you needed to do was boot the leopard instal dvd, start disk utility, and tell it to repartition the entire hard drive with one mac partition, then install normally.

---

