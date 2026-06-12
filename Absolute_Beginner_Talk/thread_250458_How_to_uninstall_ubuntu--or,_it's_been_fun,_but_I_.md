---
title: "How to uninstall ubuntu--or, it's been fun, but I have work to do and ubunto can't"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by RicardusSacerdos on 2006-09-04
I have enjoyed playing with ubuntu, but it can never replace Windows.  I have 23 years of Windows files and 18 years of PSTs, and two other computers in the house, and I cannot get to any of them with ubuntu!  So, I need to scrap the experiment.  Maybe in a few years there will be a Linux I can use without losing everything.  It's a shame, because other than the ubiquitous brown (that's what "ubuntu" really means, isn't it?), I rather liked ubuntu.

So, now I have these linux partitions on my HD.  Theoretically, I should be able to wipe them out with BootItNG, right?  Any dangers I should know about?

rs+

---

### Post by Traiger on 2006-09-04
Under XP you get options to repartition the drive so assuming you are using that then you shouldn't have any problem.

---

### Post by handy on 2006-09-04
Ubuntu is an African word meaning:

"Humanity to others"

or

"I am what I am because of who we are."

You should be able to treat the drive as unformated when reinstalling windoze...

---

### Post by anaconda on 2006-09-04
Yep. You can just wipe them avay, but remember that grub (bootloader) doesn't work when you delete the ubuntu-partition. so you have to boot with windows CD and go to recovery-console and run fixboot & fixmbr

Or boot with win98 floppy and write fdisk /mbr...

---

