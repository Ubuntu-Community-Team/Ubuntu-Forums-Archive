---
title: "Tried dual-booting vista and ubuntu get grub error 22"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by mattk132 on 2008-03-22
Hi, I tried installing ubuntu on my dad's comp.  I had some problems:(.  First of all my dad has 2 hard drives in his computer.  One is 160 gb and is his C:\ drive.  The other is an 8 gb hard drive.  I shrunk the ntfs partition with vista's partitioner to 4 gb.  I used the other 4 to make an ext3 partition and a swap partition.  The install resulted in no errors.  I then rebooted and got a grub error.  I tried to reassure my dad that I didn't kill his windows.  But he's pretty steamed.  The grub error was (grub error 22).  I am typing this on a live cd.  Any help is greatly appreciated!:(

---

### Post by Moop on 2008-03-22
You didn't kill windows. You might need to boot from the other hard drive. Go into the bios setup and change the boot hard drive to the 2nd hard drive and see if that helps. 

I'm not familiar with Vista and don't know how to restore your MBR but it shouldn't be to hard. That will get you Vista back if switching the boot hard drive doesn't work. Change the hard drive boot order back to the original before restoring the MBR. 

Super Grub disk might help.  [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by mattk132 on 2008-03-22
I tried booting off every hard drive seperately.  I get the same error.  I reinstalled grub in ubuntu using a ubuntu live cd.  I know that you can run fixmbr to solve this issue.  Unfortuneatly I don't have a dos or vista disk.:(

---

### Post by mattk132 on 2008-03-22
I also can't burn a cd because, All I can use is a live cd.:(

---

### Post by mattk132 on 2008-03-22
Thanks for all of your help.  I managed to get a vista disk. :) Just for future reference to fix it I typed in these commands into the prompt from the vista dvd:  bootrec.exe /fixmbr.  Then I typed bootrec.exe /fixboot.  This reinstalled my mbr and made my computer happy again!:)  One thing though.  How do I set this post as solved?

---

