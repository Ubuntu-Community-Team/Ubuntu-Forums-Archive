---
title: "installing and not loosing stuff on other OS"
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by neanderthal // anarchism on 2005-07-08
alright, so my computer is running on a dual boot with windblows EX-PEE and SuSe linux, i want to install my ubuntu linux OS, but i don't want to risk loosing all my stuff, how do i go about installing Ubuntu over SuSe and having a computer running windblows xp and Ubuntu without loosing anything?

---

### Post by dollydoll on 2005-07-08
Hi...this is GREAT!!! I'm a newbie to Linux, and after wandering a bunch of forums on the web, I found this one! (I feel more like...at home!and not getting looks from other people for not knowing enough)
Oh well, I do have exactly the very same problem:
Windows XP on drive C
Linux Suse 9.2 on a small drive i wanna get rid off, 
and a brand new already partioned and formatted FAT32 123Gb drive, so either Linux or Windows can read and write to it.
I would like to install Ubuntu on one the partitions of the 120Gb drive, but I'm scared of ruining what I already have in C (Windows), since my current boot loader is GRUB, and it's coming from the Suse drive...any suggestions??
Can I install Ubuntu on a FAT32 partition?
Thank you very much
Dolly

---

### Post by aysiu on 2005-07-08
Wait. You two want to install Ubuntu *over* SuSE, but you're worried about damaging your *Windows* installations?

Partitions are separations. They're separate. If you overwrite one partition (say, the Linux one), nothing happens to the other partition (say, the Windows one). Should you back up your data? Always. But you should back up your data even if you're not installing anything. Backing up should be a way of life for computer users.

As for Grub, Ubuntu will install its own Grub on the MBR, which will overwrite SuSE's Grub, and Ubuntu's Grub will recognize Windows XP, so don't worry.

---

### Post by neanderthal // anarchism on 2005-07-08
[QUOTE=aysiu]Wait. You two want to install Ubuntu *over* SuSE, but you're worried about damaging your *Windows* installations?

Partitions are separations. They're separate. If you overwrite one partition (say, the Linux one), nothing happens to the other partition (say, the Windows one). Should you back up your data? Always. But you should back up your data even if you're not installing anything. Backing up should be a way of life for computer users.

As for Grub, Ubuntu will install its own Grub on the MBR, which will overwrite SuSE's Grub, and Ubuntu's Grub will recognize Windows XP, so don't worry.[/QUOTE]


basically i need to know how to install ubuntu over SuSE like go through the default install and select whatever i need to, so i can run windblows and ubuntu and not loose anything on my windblows os

---

### Post by dollydoll on 2005-07-08
backing up?? hahahaha...I'm too lazy for that! :p but...definetely is a great idea!
my question is:
If you use the GRUB that comes with Ubuntu...you will use the MBR from Windows, and by default it'll boot on the ubuntu partition loading Ubuntu first?
thanks

---

### Post by gil-galad on 2005-07-09
Ok, n//a messeged me and I think I got him set up.  He should be enjoying ubuntu by now!

---

### Post by aysiu on 2005-07-09
[QUOTE=dollydoll]If you use the GRUB that comes with Ubuntu...you will use the MBR from Windows, and by default it'll boot on the ubuntu partition loading Ubuntu first?
thanks[/QUOTE] Either you install Ubuntu's Grub on the MBR, which means Ubuntu takes over the boot loader and sets up the dual boot option (this is a good option) or you install Grub on the Ubuntu partition, which means you have to find a way to get Windows' boot loader to recognize and dual boot with Ubuntu (a more complicated option).

---

