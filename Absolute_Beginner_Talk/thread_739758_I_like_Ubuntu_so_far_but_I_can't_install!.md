---
title: "I like Ubuntu so far but I can't install!"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by darkerlink on 2008-03-30
I downloaded the 7.10 iso and burned it onto a cd. So I get a preview of it and decide to take the final step and leave Windows XP for good! I double click "Install" and go through the process of choosing drives. I choose the main drive(a 40 gb hd) and clicked next up until it says "Ready to Install". I click "install" and it pops up, "Starting the partitioner", "Installing System" then BAM! "Failed to create a file system" "The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed."

So am I doomed to live with the evils of Microsoft? I am lost at this point. I thought I must have did something wrong. I selected the option of "Guided - Use entire disk". I thought the nightmare was going to be over. Someone please wake me up!

---

### Post by Hutom on 2008-03-30
Is it a live cd or an alternate cd (i.e. text-based installer)?

---

### Post by Inxsible on 2008-03-30
> **darkerlink said:**
> I downloaded the 7.10 iso and burned it onto a cd. So I get a preview of it and decide to take the final step and leave Windows XP for good! I double click "Install" and go through the process of choosing drives. I choose the main drive(a 40 gb hd) and clicked next up until it says "Ready to Install". I click "install" and it pops up, "Starting the partitioner", "Installing System" then BAM! "Failed to create a file system" "The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed."

So am I doomed to live with the evils of Microsoft? I am lost at this point. I thought I must have did something wrong. I selected the option of "Guided - Use entire disk". I thought the nightmare was going to be over. Someone please wake me up!Not sure if it will definitely help, but you can start up GParted from System>>Administration>>GParted and first format the drive to ext3 and then try installing.

Although starting a direct installation has been known to work. You can still try however.

You may also want to dual boot, that way you can keep Windows around just in case.

---

### Post by seshomaru samma on 2008-03-30
I suggest dual booting Windows and Linux until you feel comfertable with Linux
use gparted to reisze the Windows partition and create a new Linux partition ,there are many ways to part the disc, so please read the explnation[ here]("http://www.psychocats.net/ubuntu/partitioning")
and about[ installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by darkerlink on 2008-03-30
Thanks guys. I found the problem. At first, ubuntu didn't recognize the OS on the HD. I gave up and decided to restart and go back to windows xp when I got a message that said, "NTLDR not found" I was scared. Booted up the Ubuntu disk and now it recognizes the OS and installation was fine! A huge learning curve I must say. A few program I needed were absolutely essential but I couldn't run EXE files. I found out I needed WINE and ran the windows programs just fine! One small thing and maybe I am being picky but the WINE emulation makes the Windows XP programs look god-awful. Is there a way for WINE emulate programs seamlessly with Ubuntu? I love the Ubuntu look but switching to the ugly DOS type interface makes me grind my teeth.

---

### Post by stalkingwolf on 2008-03-30
depending on what programs you want to run Crossover Linux might be a better choice than
wine.  In any case there are choices.

---

### Post by seshomaru samma on 2008-03-30
Ii think it would be better to look for Linux native alternative to your Windows programmes
but it is possible to make Wine aps look nicer , read here: [http://ubuntuforums.org/showthread.php?t=142741](http://ubuntuforums.org/showthread.php?t=142741)

---

