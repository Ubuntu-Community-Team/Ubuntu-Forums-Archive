---
title: "can i use alternate download to run ubuntu from CD w/out installing it?"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by stef_204 on 2006-08-28
Hi guys,

brand new to ubuntu but looking forward to it.

can i run ubuntu from the cd without installing it (just to try)  using the alternate download ubuntu-6.06.1-alternate-i386.iso OR MUST i choose the ubuntu-6.06.1-desktop-i386.iso?

If i do end up installing ubuntu on my hard drive, then--4 various reasons--i will use the alternate download for the hard disk ubuntu-6.06.1-alternate-i386.iso (that i have already burned to a CD.)

since i do not want to download both the alternate and desktop images, if not needed, just wanted to check.

tx a lot!

---

### Post by bodhi.zazen on 2006-08-28
No

---

### Post by kinematic on 2006-08-28
the desktop cd is the live cd(from wich you can also install)and the alternate cd is a text based installer wich gives greater configureability or you can use it to install on older systems with not so much ram.

---

### Post by tht00 on 2006-08-28
Desktop cd:  Live CD with an installer located on the Desktop.  The good: fastest instal, plus, you can preview Ubuntu and take a look around while you install it.  The bad: not recommended for older machines.

Alternate cd:  Text-based installation.  The good: works best on older machines.  Might work in the case the desktop installation would fail.  The bad: slower.  Completely ties up the use of the computer.

I hope that explains it better.

---

### Post by stef_204 on 2006-08-28
OK, got it.

the reason i downloaded the alternate i386 iso is because of this article: [http://www.terabyteunlimited.com/kb/article.php?id=279](http://www.terabyteunlimited.com/kb/article.php?id=279)

see section on the MBR.

so i will have to also download the regular i386 desktop iso; then try ubuntu with that and if want to do hard disk install, go back to the alternate i386 iso if above article from terabyte is correct.

tx.

---

### Post by tht00 on 2006-08-28
hmm... I never caught that, though, I always install GRUB, and it does a fine job of setting everything up.

What do you plan on using instead of GRUB?

---

### Post by stef_204 on 2006-08-28
I do plan to use GRUB.
just want to make sure it doesn't overwrite MBR.

quoting the article: "It will always install GRUB to the MBR and overwrite both the MBR and EMBR without asking.......

In order to have a choice about where to install GRUB, it is recommended that BootIt NG users use the "Alternate Install CD" instead.  Doing this will prevent the possible loss of partitions on HD0."

haven't researched what the exact alternative is, i.e. WHERE to install GRUB so doesn't overwrite MBR, etc.

once i have tested ubuntu via the desktop cd, i basically will want to install ubuntu in a way that is the least intrusive possible, leaves win xp as my main boot system, doesn't alter a/g (boot issues, MBR, etc.) until i am more comfortable with it and selectively start using it more and more.

---

### Post by toasted on 2006-08-28
Even if you use the live cd, you can dual boot, I do. I have 2 installs of Ubuntu on my machine and XP too.. they all work. If for some reason you want to remove Ubuntu and go back to Windows you can restore the mbr with the XP cd. It is covered many times in these forums.

---

### Post by stef_204 on 2006-08-28
i dt have the XP cd to restore since my machine is an OEM version with only recovery disks.
it seems safer to me NOT to have the MBR overwritten....
i imagine no such thing happens if one just runs ubuntu from the cd; and that this becomes an issue only upon hard disk install, correct?

---

### Post by toasted on 2006-08-28
100% correct
As long as you only run the live cd and do not install, there is no changes made to your system.

I would advise getting an XP install disk if you want to keep on using it. Sooner or later you WILL need it... trust me on that. 

If you decide to install Ubuntu there is always a risk of losing data. Make sure you back up anything you don't want to loose!!!  with some more !!!!!!

---

### Post by stef_204 on 2006-08-28
u'r so right.
i have recently made full backups of all my data, so i hope to be OK.

i just have 1 more question with regards to ubuntu and FAT32 and NTFS.

i'll open another thread for that.  tx to all that replied.

---

