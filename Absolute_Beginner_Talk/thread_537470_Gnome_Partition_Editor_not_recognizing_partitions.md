---
title: "Gnome Partition Editor not recognizing partitions"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by verticalgain1 on 2007-08-28
I've had Feisty running stable for about a week.  Today I decided to try and install Windows XP in the 40 gig empty partition on my drive.  I booted from a CD and ran a program called Fdisk Extended I believe, that reformatted the empty part to FAT32.  I did not adjust my Linux partitions.

The Windows didn't work like I wanted it to, so I uninstalled and reformatted that section of the drive again.  Only the Windows partition.

When I rebooted the computer GRUB loaded just fine and put me right back into Feisty on my main partition.  It runs fine.  I've got no glitches or bugs, and I've restarted and logged in/out a few times now.

I want to reformat my FAT32 partition to a Linux partition.  Not for my current Ubuntu but for a seperate gaming install.

*****HERE IS MY PROBLEM:::::::

When I open Gnome Partition Editor it shows my entire disk (80GB) as being unallocated.  It worked fine before I formatted the other partition.  My current partition with the working Feisty is around 30G.  I really need all the space I can get and would really appreciate any help.

I REALLY don't want to reinstall.  Fixing this can't be as bad as reprogramming the whole thing from the beginning to work with my stuff.

---

### Post by reset3x on 2007-08-28
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by verticalgain1 on 2007-08-28
Thanks for the response, but could you be more specific in how that walk through addresses my problem?

I am not trying to dual boot with Windows.  I tried it and now my Linux Gparted says my entire drive is unallocated.  What I am trying to do now is get my partition structure to recognize so I can install a second linux partition.

If the guide you posted tells me how to do that I'm not seeing it.  I have read through the FAQ's and have yet to figure this out.

---

### Post by ramjet_1953 on 2007-08-29
If you haven't already done so, download the [COLOR="Blue"]GParted LiveCD.[/COLOR]

It is an iso that you burn to a CD and then you boot your system from it.

It is very good and will overcome most formatting problems.

Here is a link for the latest download: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Don't forget to burn the iso SLOWLY, no faster than 4 X.

Regards,
Roger :cool:

---

### Post by reset3x on 2007-08-29
> **verticalgain1 said:**
> Thanks for the response, but could you be more specific in how that walk through addresses my problem?

I am not trying to dual boot with Windows.  I tried it and now my Linux Gparted says my entire drive is unallocated.  What I am trying to do now is get my partition structure to recognize so I can install a second linux partition.

If the guide you posted tells me how to do that I'm not seeing it.  I have read through the FAQ's and have yet to figure this out.


Yopur best bet is to install Windows first... Then defag Windows... Then install Ubuntu.... The Install Menu will guide you through the process......

---

### Post by verticalgain1 on 2007-08-29
> **reset3x said:**
> Yopur best bet is to install Windows first... Then defag Windows... Then install Ubuntu.... The Install Menu will guide you through the process......

Again, I am NOT trying to install Windows.  I have downloaded the Gparted live CD and will be trying that next.

---

