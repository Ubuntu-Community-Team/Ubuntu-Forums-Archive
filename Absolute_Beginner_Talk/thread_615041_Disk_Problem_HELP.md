---
title: "Disk Problem HELP"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by federicotedin on 2007-11-16
I have a 160 GB HDD, i deleted the Ubuntu partition because i am going to install it in another computer, i deleted the SWAP, ununstalled GRUB, and i got 45 GB empty unllocated.  I tried making the windows partition bigger but i always got an error.  I rebooted from the Live CD and now the Gparted only detects the windows part of my HDD, but not the unlocated part.  I cant expand my windows partition now, what can i do?
HELP
thanks

---

### Post by federicotedin on 2007-11-16
please help

---

### Post by Sims2789 on 2007-11-16
> **federicotedin said:**
> I have a 160 GB HDD, i deleted the Ubuntu partition because i am going to install it in another computer, i deleted the SWAP, ununstalled GRUB, and i got 45 GB empty unllocated.  I tried making the windows partition bigger but i always got an error.  I rebooted from the Live CD and now the Gparted only detects the windows part of my HDD, but not the unlocated part.  I cant expand my windows partition now, what can i do?
HELP
thanks

Microsoft claims ([http://support.microsoft.com/kb/329826](http://support.microsoft.com/kb/329826)) that installing SP2 will fix it, but NTFS is notorious for issues with changing partition sizes.

Reinstalling Windows would always fix it, but I assume you don't want to do that.

Also, you could always create new a NTFS partition in the unallocated space. I know this isn't a solution, but at least you could use your entire hard drive.

---

### Post by federicotedin on 2007-11-16
Thanks, but the problem is that i cant create a new partition, as now Gparted AND windows only 'see' the 102GB NTFS partition, and the 58 GB remaining arent detected neither by Gparted or Windows, so i cant do anything with it.  Isnt there a way to re-detect the empty part og my HDD?
help thanks

---

