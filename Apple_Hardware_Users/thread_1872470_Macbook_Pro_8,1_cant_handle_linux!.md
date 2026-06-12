---
title: "Macbook Pro 8,1 cant handle linux!?"
date: 2011-10-30
forum: Apple Hardware Users
---

### Post by gfunkera on 2011-10-30
Going nuts tryna find the answer. Got a macbook pro that i want linux on. the specs are as follows:
```
**Hardware Overview:**

  Model Name:	MacBook Pro
  Model Identifier:	MacBookPro8,1
  Processor Name:	Intel Core i7
  Processor Speed:	2.7 GHz
  Number of Processors:	1
  Total Number of Cores:	2
  L2 Cache (per Core):	256 KB
  L3 Cache:	4 MB
  Memory:	4 GB

**OS === LION!**
```

Im going crazy trying to find a way to make this thing run linux. i cant run a live cd, every version of linux i have tried fails to run a live distro. also, the ***rEFIt thing doesnt work*** with these macs, either. there is NO INFORMATION that works anywhere out there.

[SIZE="4"]have any of you guys figured this out yet? please help.[/SIZE]

---

### Post by B Pearce on 2011-11-04
Hey [gfunkera]("http://ubuntuforums.org/member.php?u=822615"),

I had similar issues, and have the same model computer as you (An Early and a Late 2011 Macbook).

Here is the scoop; Ubuntu started releasing ubuntu...+mac.iso images because the livecd's were not booting, this is due to the Mac using a bazaar EFI specification...

The 64bit, standard version of Oneiric will boot just fine, but you have to do a few things:

1. Boot using refit and synchronize your partition table, you can do this by selecting the little disk icon next to the terminal icon when rEFIt boots.

2. Boot from the livecd by holding down the alter key at boot (not using refit) and selection EFI boot with the CD icon.  This will boot oneiric using GRUB EFI and will allow you to boot and install.

3. Be warned: Once oneiric has installed the hidden EFI partition on your HD will have a bootloader installed in it; you have to use rEFIt and select boot EFI.  The icon looks like three cubes.

4. Don't format or delete this partition, let GRUB do its magic, if you format this partition you risk never being able to modify your partition structure or booting; note that Ubuntu is far more resilient to this than Mac OS is.

All the best, really hope this helps,

Brad

---

### Post by gfunkera on 2012-01-28
**BUMP**

B Pearce,

That doesnt work.

Has this issue been resolved yet?

---

### Post by peter rus on 2012-01-29
gfunkera, we would need to have a more detailed specification of your problem, just 'the refit thing doesn't work' is not enough, what is 'the refit thing' and what doesn't work.

@B Pearce, as seen in my thread @ [http://ubuntuforums.org/showthread.php?t=1915483](http://ubuntuforums.org/showthread.php?t=1915483) I am not able to properly boot those +mac images either. Also rEFIt partition table sync does not seem to work.

---

### Post by tgeulin on 2012-01-29
> **gfunkera said:**
> Going nuts tryna find the answer. Got a macbook pro that i want linux on. the specs are as follows:
```
**Hardware Overview:**

  Model Name:	MacBook Pro
  Model Identifier:	MacBookPro8,1
  Processor Name:	Intel Core i7
  Processor Speed:	2.7 GHz
  Number of Processors:	1
  Total Number of Cores:	2
  L2 Cache (per Core):	256 KB
  L3 Cache:	4 MB
  Memory:	4 GB

**OS === LION!**
```

Im going crazy trying to find a way to make this thing run linux. i cant run a live cd, every version of linux i have tried fails to run a live distro. also, the ***rEFIt thing doesnt work*** with these macs, either. there is NO INFORMATION that works anywhere out there.

[SIZE="4"]have any of you guys figured this out yet? please help.[/SIZE]


I got refit installed on my os x lion macbookpro8,2 by installing it manually
in order to boot from the linux live cd, you must have both a live cd and a live usb.
check out this thread [http://ubuntuforums.org/showthread.php?t=1908210](http://ubuntuforums.org/showthread.php?t=1908210)
its how i triple booted my macbookpro8,2 but it might answer some of your questions as well.

---

### Post by into_311 on 2012-03-05
I don't want to INSTALL Ubuntu I just want to boot the LIVE CD. I have yet to find a solution that works for me on my Macbook Pro 8,2 model though. It starts loading the ISOLINUX image and just hangs there on a blinking cursor...

---

