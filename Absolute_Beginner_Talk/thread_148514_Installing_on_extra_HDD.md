---
title: "Installing on extra HDD"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by shador on 2006-03-22
Im thinkin of installing ubuntu on my extra 8GB HDD. But how am I supposed to do with installing GRUB and stuff like that. Won't the bootup process be fucked up if I have two OS on different HDD's?

---

### Post by Aewheros on 2006-03-22
Grub is by default always installed to the boot sector of your first hardrive,
regardless of where you install Ubuntu. Shouldn't be any problems.

---

### Post by localzuk on 2006-03-22
What is currently on your existing hard disk? Is it windows or Ubuntu? Ubuntu should be able to manage any number of OS's installed on any number hdd's - you will just end up with a menu.

When asked, let grub be installed on the primary hard disk master boot record (MBR) - else you will not get the grub menu.

---

### Post by Mustard on 2006-03-22
If you are really worried about it then you can physically disconnect the first hard drive, and install ubuntu with just the second hard drive going.  Your bios may support a boot menu at start up and after reconnecting the first drive you could use that to choose which operating system you want to load. Another option would be to manually change the boot order in bios each time you want to switch operating systems.

Alternatively again, you could practice a bit first with installing grub manually on a system, so that should anything go wrong, you have some idea what you are doing.

If you are really worried about the consequences, then there is probably a good reason for you to worry ie you have no idea what you are doing, you can't afford to be without your other operating system for any length of time and many more good reasons why you shouldn't install now. :)  Preparation and caution is a good thing.  Read first, think about solutions that you feel comfortable with, and only proceed when you feel confident of the outcome.

---

### Post by shador on 2006-03-22
So basically it doesn't matter on wich HDD i install Ubuntu, as long as I install GRUB on the primary, right? 

BTW, thanks for the quick answers :)

---

### Post by Mustard on 2006-03-22
[QUOTE=shador]So basically it doesn't matter on wich HDD i install Ubuntu, as long as I install GRUB on the primary, right? 

BTW, thanks for the quick answers :)[/QUOTE]

Yeah, basically.  If you have both drives connected, then you will instruct the installer to use the second drive, and after formatting and partitioning it will install grub on the MBR of the first drive.   Grub will give a menu showing which operating systems you can choose to boot and will handle the booting for you.

There is always more than one way to skin a cat with linux too.  Again if you are really worried about the implications of any complications that could arise, you can use a range of live CD's to make images of your first drive and make backups of the MBR (storing them on seperate media of some kind) and if the worst does happen, you can restore the partitions and the MBR to the way it was when you began.

Something like Partimage on a live CD is perfect for this job, and is relatively simple to do.  This is their website [http://www.partimage.org/](http://www.partimage.org/) you might like to read over the documentation and read over the forums to see what type of issues people have with partimage.

All this is a lot of work for what is probably a very small chance of failure in the installation.  Nevertheless maybe you can't afford any risk of failure.  If thats the case, then do things the long way and don't take the chance. :)

You can also restore the MBR of a windows XP installation with the XP install disk in rescue mode using the command fixmbr.  This will totally wipe grub and you won't be able to boot into ubuntu using grub anymore, unless you reinstall it manually.  Installing grub manually can be troublesome at times. I much prefer leaving it to the installer.

---

