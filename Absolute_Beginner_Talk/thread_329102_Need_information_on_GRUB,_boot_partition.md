---
title: "Need information on GRUB, /boot partition"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by Enkra on 2006-12-31
I am new to Linux/Ubuntu and need a better understanding of Grub, MBR, and /boot partition. I did a few search and read a few HOW-TOs on the topic but none really fuly answer my question(s).


I have 1 hard drive with 3 partitions: sd0(ntfs), sd1(ext), and swap.

At one point when installing ubuntu, I was asked if I want to install GRUB in MBR or /boot partition. Well in my case I pick to install GRUB in MBR. Now the question is, does ubuntu install GRUB in MBR and then install GRUB in /boot partition too because I see there's a /boot/grub directory when I browse around?

If GRUB is installed in the MBR, why is there a /boot/grub directory on the linux filesystem? What does the /boot/grub directory there for?

What if I pick to install GRUB in /boot partition, will I still be able to boot to linux?


Sorry if there questions sound stupid but I am kinda confused and really want to learn.


Thanks,
Enkra

---

### Post by riven0 on 2006-12-31
:confused: Actually Grub should be in the /boot directory. Are you by chance doing a dual-boot? Does Ubuntu and XP boot up okay?

---

### Post by Sigudian on 2006-12-31
i think that the /boot/grub files are just new install files for GRUB, but im not sure
[this site]("http://en.wikipedia.org/wiki/GNU_GRUB") might answer some questions

---

### Post by jem7v on 2006-12-31
The /boot/grub files are where GRUB lives, to the best of my knowledge (though I Could be wrong about that one).  And your Linux kernel will be in /boot.  If you're running with an older computer - i.e., one where the BIOS won't boot from a file deeper than 8 gigs into your hard drive - then it's particularly handy to have a /boot partition right at the start of your drive to make sure it doesn't save a kernel update too deep for your BIOS to boot from.  (I figured this out the hard way.)

---

### Post by handy on 2007-01-01
The MBR is a very small amount of space on your hard disk drive. All that is there is the minimum amount of info' pointing to your partition table, identifying file systems & allowing GRUB to access it's config' files elsewhere on a hard disk drive.

Think of it like a the boot block of a floppy, the first part of the disk to be read that contains crucial pointers.

---

### Post by Enkra on 2007-01-01
> **riven0 said:**
> :confused: Actually Grub should be in the /boot directory. Are you by chance doing a dual-boot? Does Ubuntu and XP boot up okay?

No right now I just install Ubuntu on Sd1 partition. Plan to install Windows XP in the near future though.

So from my understand from reading the replies so far is that GRUB is install in the MBR but /boot/grub is a directory where grub files reside. BUT does those files do anything to help boot up linux? or it's just there for backup because the GRUB that is installed in the MBR is the one that actually  boot up the kernel right? 


Also, can anyone answer this specific question:
What if I pick to install GRUB in /boot partition, will I still be able to boot to linux?

---

### Post by Enkra on 2007-01-01
> **handy said:**
> The MBR is a very small amount of space on your hard disk drive. All that is there is the minimum amount of info' pointing to your partition table, identifying file systems & **allowing GRUB to access it's config' files elsewhere on a hard disk drive**.

Think of it like a the boot block of a floppy, the first part of the disk to be read that contains crucial pointers.

Could it be that the config' files that GRUB access reside in the /boot/grub dir?

---

### Post by handy on 2007-01-01
Yes, the **menu.lst** file.

---

