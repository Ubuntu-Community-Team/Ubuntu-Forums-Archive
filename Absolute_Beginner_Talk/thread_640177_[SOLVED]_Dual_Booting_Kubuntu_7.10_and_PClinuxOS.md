---
title: "[SOLVED] Dual Booting Kubuntu 7.10 and PClinuxOS"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by patrickaupperle on 2007-12-13
I know this has been posted before, but I did some searching and could not find anything:confused:

I have Kubuntu 7.10 installed on my hard drive and read a few reviews and decided I wanted to try PClinuxOS.

If anyone could point me to a good guide for dual-booting kubuntu and PClinuxOS I would appreciate it.

Thank you in advance:)


Oh yeah one more thing, my install is fresh so deleting it is no prob. If it is easier to dual boot with pclinuxos on the hard drive first then I have no prob going that rout.

---

### Post by Nano Geek on 2007-12-13
Any modern Distrobution shouldn't have any problem automatically setting up a dual-boot. 
Just make sure you shrink your Ubuntu partition on your HDD instead of deleting it.

---

### Post by Incense on 2007-12-14
Yeah, as long as you have a free partition, then just go for it and the end result should be a grub menu with both distros as options. In the end you will use PCLOS's bootloader, but it should not have a problem detecting ubuntu.

---

### Post by louieb on 2007-12-14
Two bits worth  of experience:
Set up GRUB to chainload or use the configfile option to run the PCLinuxOS Grub boot menu. [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

Use Gparted to create the install partition ahead of time. PCLinuxOS uses DiskDrake. DiskDrake can alter the partition table in a non-standard way. GParted can be run from the [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

I kinda liked PCLinuxOS as a KDE desktop its not bad. But I prefer Gnome

---

### Post by patrickaupperle on 2007-12-14
Thank you for all of the wonderful replies:KS
The Ubuntu forums are always  so helpful
:guitar:

I just have to make two things clear before I do anything. 

1. You are saying that i just need to shrink my Ubuntu partition, or are you saying that I need to shrink my Ubuntu partion and create a new one for PClinuxOS? If I need to create a second partition then what file system should I use? :confused: 

2. Can I delete the extra partition if I decide I do not like PClinuxOS?

---

### Post by IgnacioMiller on 2007-12-14
I highly recommend using the GParted livecd to prepare a free partition beforehand. In my experience it just makes things easier and less of a headache.

---

### Post by Incense on 2007-12-14
> **patrickaupperle said:**
> Thank you for all of the wonderful replies:KS
The Ubuntu forums are always  so helpful
:guitar:

I just have to make two things clear before I do anything. 

1. You are saying that i just need to shrink my Ubuntu partition, or are you saying that I need to shrink my Ubuntu partion and create a new one for PClinuxOS? If I need to create a second partition then what file system should I use? :confused: 

2. Can I delete the extra partition if I decide I do not like PClinuxOS?

1. If you do not already have a free partition, then yes you will need to use gparted to shrink your ubuntu partition to allow enough free space to make a new partition. You can share your exsisting swap partition (and home if you have one) between the two distros. I would use EXT3 as the file type. 

2. Yes you can always remove the partition and install a different distro, or reclaim the space for Ubuntu using gparted. 

Please note though, **always back up vital data before altering your partitions**. Things generaly go smoothly, but you never know when you'll hit the wrong button and delete everything.

---

### Post by Nano Geek on 2007-12-14
> **Incense said:**
> Please note though, **always back up vital data before altering your partitions**. Things generaly go smoothly, but you never know when you'll hit the wrong button and delete everything.This cannot be stressed enough.

Before any partitioning or installing happens, **back up your data**.

---

### Post by patrickaupperle on 2007-12-14
Once again thanks.

I bet my friend he could go till Christmas without using windows and only using Kubuntu.
He "borrowed" my Kubuntu computer and said I could use his windows box.
I cant try these solutions till Christmas for the above reasons, but thanks for the solutions.
I am sure they will work great :)

---

### Post by Incense on 2007-12-14
> **patrickaupperle said:**
> Once again thanks.

I bet my friend he could go till Christmas without using windows and only using Kubuntu.
He "borrowed" my Kubuntu computer and said I could use his windows box.
I cant try these solutions till Christmas for the above reasons, but thanks for the solutions.
I am sure they will work great :)

Ah, windows isn't so bad. Just install [Win-Get]("http://windows-get.sourceforge.net/index.php") to grab all your open source goodness, then install [Clearlooks for Windows XP ]("http://schmoove.deviantart.com/art/ClearLooks-for-Windows-XP-18591720"), install [Cygwin]("http://www.cygwin.com/"), and find a nice wallpaper on [http://www.kde-look.org/]("http://www.kde-look.org/") or [http://www.gnome-look.org/]("http://www.gnome-look.org/") and you should be able to go the couple weeks with only minimal madness. ;) Point your mate in our direction if he needs any help with Kubuntu.

---

### Post by patrickaupperle on 2007-12-15
> **Incense said:**
> Ah, windows isn't so bad. Just install [Win-Get]("http://windows-get.sourceforge.net/index.php") to grab all your open source goodness, then install [Clearlooks for Windows XP ]("http://schmoove.deviantart.com/art/ClearLooks-for-Windows-XP-18591720"), install [Cygwin]("http://www.cygwin.com/"), and find a nice wallpaper on [http://www.kde-look.org/]("http://www.kde-look.org/") or [http://www.gnome-look.org/]("http://www.gnome-look.org/") and you should be able to go the couple weeks with only minimal madness. ;) Point your mate in our direction if he needs any help with Kubuntu.


win-get?

What kind of apps can or should I get?



And how do I "install [Clearlooks for Windows XP ]("http://schmoove.deviantart.com/art/ClearLooks-for-Windows-XP-18591720"), install [Cygwin]("http://www.cygwin.com/")"

---

