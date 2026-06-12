---
title: "[SOLVED] Can I create a small Windoh's partition?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by victor9098 on 2007-11-01
Hello All,

Been using Ubuntu since June now but I have hit a wall with some software I need to use.

WINE is not able to help me, so is there a way for me to add a Windows XP partition (dual boot?) just for these 1 or 2 applications. Maybe only 10GB in size! 

I have a XP Home Edition (somewhere!?).

Any advice would be great! Thanks.

---

### Post by maybeway36 on 2007-11-01
You can use a live CD with GParted to shrink your Linux partition, then make a partition for windows. After installing, reinstall GRUB (not sure how, but other people can help you with that.)

---

### Post by victor9098 on 2007-11-01
Have been looking for a 'How To' but can not find any. All the documentation seems to deal with making a Ubuntu Partition/Dual Boot on a Windows machine.

I have a bad feeling that it might not be worth the risk...

I have the Live CD from 7.04, I have upgraded to 7.10, any idea if it would be ok to use that? Will I lose information?

---

### Post by Incense on 2007-11-01
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

Create the partition, install windows on it, then follow that guide.

---

### Post by Arthur Archnix on 2007-11-01
What are your system specs? I ask because if they're ok, then maybe virtualization is a better option.

Edit: PS. INsense,  love your avatar. ;)

---

### Post by victor9098 on 2007-11-01
Great Advice, Thank you...

My specs are:
Intel Core 2 Duo, Processor T5500 (1.66Ghz)
1GB DDR2 SDRAM
Intel GMA 950

Silly question...any good guides to help with the creation on the partition and installation of Windows (If virtualization is not an option)?

Thanks again!

---

### Post by Arthur Archnix on 2007-11-01
Oh yeah, you're laughing. That's the same system as I have. Virtual box is a dream. The latest version even seamlessly integrates into your desktop so that running apps (like say SPSS) look at home in Ubuntu even though they're running in a virtualized os like XP.

Try that before resizing. Anyway, I've resized before and never had problems, but it's always a good idea to back up your data. Then I use the gparted live cd. Free up space at the start of the drive, not the middle or the end. Format it to NTFS. When you insert your windows cd let it reformat ntfs and not quick format.

---

### Post by louieb on 2007-11-01
Run Gparted my favorite  is to use the  [SystemRescueCd]("http://www.sysresccd.org/Main_Page")
Heres a good site on how to use [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")
You will shrink Your Ubuntu partition by whatever. ( I have XP home on an 8 gig partition). 
Use the unallocated space to create a** primary **partition format it NTFS.
Install XP 
XP will replace GRUB in the MBR you need to put GRUB back and make it boot XP to. [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm") or [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/")
Your done. Good luck.

---

### Post by Incense on 2007-11-01
Seeing your specs, I would have to second the virtual box suggestion. It would be a lot easier, and faster. Give it a go!

---

### Post by victor9098 on 2007-11-02
There is hope yet then!

I have downloaded Virtual Box and I am trying to set it up...getting errors that it can not detect hosts!

Will keep at it and google for a few "how to's".

Thank you all for the help! Will update later!

---

### Post by victor9098 on 2007-11-02
It could only happen to me...

I got my first Win-doh's pc back in 95...ever since them I have got upgrade packs or it has been bundled on new machines, I do not have a single FULL copy, even after spending €€€€'s on the damn stuff...oh yeah, that is why I am using linux now!

Anyway, been to Amazon and have found a copy of Windows 98, I do not have any other choice?

Thanks again

---

### Post by jr.gotti on 2007-11-02
> **victor9098 said:**
> It could only happen to me...

I got my first Win-doh's pc back in 95...ever since them I have got upgrade packs or it has been bundled on new machines, I do not have a single FULL copy, even after spending €€€€'s on the damn stuff...oh yeah, that is why I am using linux now!

Anyway, been to Amazon and have found a copy of Windows 98, I do not have any other choice?

Thanks again

Small typo I noticed....it's Windows ;)

---

### Post by victor9098 on 2007-11-02
My bad! [-X

---

