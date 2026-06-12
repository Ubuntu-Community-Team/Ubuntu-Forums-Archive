---
title: "cannot load ubuntu from the hard disk - always get xp"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by shumboom on 2008-02-12
I have installed ubuntu to a hard disk but my dell refuses to load from it or to offer me the option of loading it. What I get is a series(10 I think)  of options of loading Windows xp, 1 is load normally,2 (in italian) is if this fails try this, 3, more of the same.etc.

I have reinstalled windows since (on a different hard disk) but this menu always appears when booting. I remember installing a utility when I had a major problem booting into windows and I got this. But after the bug went away I never saw the menu again so I am guessing that the Ubuntu install has woken this file up.

Even attempting to boot off the hard disk with the ubuntu cd in still brings up the 10 xp options. What should I try next?

thanks,SHumit

---

### Post by jhenager on 2008-02-12
First of all, I would check the boot order in the BIOS (computer startup).
If the CD is your first boot device, it should never even see the HD.
Secondly, it sounds like something has replaced Grub or Lilo (whichever you are using).
Get a copy of the Super Grub disk, or GrubEd.

---

### Post by Tatty on 2008-02-12
The reason it wont boot from the CD is probably because you have the hard disk set to a higher boot priority in your bios.  On your next boot, go into the bios and make sure it checks the CD for an operating system before the hard disk.

As for not booting ubuntu from the hard disk, im afraid i cant really help you there as I have never had any such problems myself.  

Although it sounds like a problem with the GRUB - in that it doesnt appear to be loading.

---

### Post by skippi90 on 2008-02-12
Well if it is showing the XP bootloader, then the simple thing to do if it isn't your BIOS causing the problems would be to edit the XP bootloader to include Linux. I have my linux distro's in my Vista Bootloader.

---

### Post by shumboom on 2008-02-13
hi, 

that seems to be the best option. But what is the line I need to type into the boot file to add ubuntu?

thanks, shumit

---

### Post by rkd on 2008-02-13
This web page:

[http://www.tprthai.net/bootmgr.htm](http://www.tprthai.net/bootmgr.htm)

gives directions for setting up to have Windows' boot manager let you boot your Linux partitions, too.

There are lots of other places that give directions for this -- it took one simple, quick Google search to find a ton of them, so if you don't like this one, a quick search will give you others to look at.

I can't guarantee that this will solve your problem, since most people don't have this problem happen to them. That tells me your computer is set up differently somehow. Whatever that difference is might make the usual directions for having the Windows boot manager boot the Linux partitions also not work.

---

