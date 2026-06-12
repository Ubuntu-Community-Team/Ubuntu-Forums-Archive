---
title: "Windows or Linux to Come first in a partitioned hard drive?"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Vapourstreak on 2008-01-20
I'm partitioning my 200GB hard drive so I can fit Ubuntu and Windows XP Pro on it.  I have divided the hard drive in half using GParted, but I'm wondering which format I should format the hard drives, to.  Should I use NTFS (for Windows) or ext3 (or Ubuntu)?  Which one is better?  Which one should I do?  I want to use GRUB.

i need a quick reply because I need to finish installing both os's by tonite (vancouver time)

BTW, is there anyway to have the GRUB menu appear when you boot up, instead of pressing any button when it tells me to?

Thanks,
Vapourstreak

---

### Post by Rog-Mahal on 2008-01-20
You will need to use both formats: NTFS for windows and EXT3 for Linux. However, when you install the OSes they will probably reformat their respective partitions anyway. I recommend installing XP first and then Linux because Windows doesn't like to recognize other operating systems in the boot menu. Hope that helps!

---

### Post by JoshuaRL on 2008-01-20
First of all, I've heard that Super Grub makes loading and configuring grub really easy.  So you might try that.  Also, I believe that Windows likes to be the first partition.  So if you're going to load it, you may as well load it there.  You can still edit grub to read Ubuntu as the default OS to load on startup, while having Windows as the first.  And I think that the partition types you have there will work for the respective OS.

---

### Post by CupofDice on 2008-01-20
You format Windows in ntfs and Ubuntu in ext3 SEPARATELY. Each partition (the one for windows and the one for ubuntu) will have two different file systems. I am assuming you don't have an OS installed on the comp right now? If you have windows already installed, and you don't want to get rid of it, then do not format the ntfs side, but it seems like you don't have windows installed, so just do what JoshuaRL and Rog-Mahal says.

---

### Post by Vapourstreak on 2008-01-20
okie.  Windows xp will be first.  

thanks

---

