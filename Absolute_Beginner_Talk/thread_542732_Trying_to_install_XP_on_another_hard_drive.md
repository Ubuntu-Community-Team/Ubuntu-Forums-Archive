---
title: "Trying to install XP on another hard drive"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by toolfreakuna on 2007-09-04
Hello all,

I have been using Ubuntu for about a week now, and am really enjoying it. However, due to school work which needs me to use Microsoft Visual Studio (ick) and also because I like to game, I was going to install Windows XP on another hard drive. I have two IDE drives, a 30 GB and a 80GB, and also a 500 GB SATA drive (this is where Ubuntu is installed). 

However, when I try and install XP, it tells me that I can't install it on either of the IDE drives since they aren't formatted for XP. When I create a new partition in the XP setup, I receive the same error message. Any suggestions would be helpful.

Thank you.

---

### Post by Miguel on 2007-09-04
Which one is the primary drive? As far as I know, Windows wants to be on the first hard drive, so you might need to swap discs or change the order in the BIOS. I can't help you much more, as my experience with multi-drive setups is limited.

---

### Post by toolfreakuna on 2007-09-04
Okay, I will try changing the BIOS options.

---

### Post by Miguel on 2007-09-04
Remember you might need to restore the settings should grub not work!!!

---

### Post by toolfreakuna on 2007-09-04
Okay, when I tried to install XP this time, after the initial copying of files, it rebooted only to say:

Disk Error
Press any key to restart

I pressed enter, and Ubuntu loaded. Any suggestions?

---

### Post by Miguel on 2007-09-04
No, I haven't. The only other thing I imagine is opening the box and swapping the drives, but this won't probably work because of different interfaces. Sorry.

---

### Post by rsambuca on 2007-09-04
What is the boot order of your drives in the BIOS?

---

### Post by stalkingwolf on 2007-09-04
As I recall you will have to install XP first ( even if on seperate drives).  Then install Ubuntu.  The xp
drive must as I recall be jumpered as "primary master" and the next drive (ubuntu )as" primary slave".
Install you win OS on the primary master drive and Ubuntu of the slave drive.  You can later change the boot sequence in the Grub boot list to which ever system you wish to boot first.

Changing the order in the bios or setup menu only changes the hard ware order.IE: mine is set to boot
CD/DVD, Floppy, HDD.

---

### Post by rsambuca on 2007-09-04
The ubuntu drive is  SATA - no jumpers!

---

### Post by bobpur on 2007-09-04
Everyone is right telling you to install Windows first. If you don't windows will overwrite grub and render linux unusable.
I would forget the IDE drives and partition the SATA drive for both operating systems. That's 250 gb as NTFS and about 248 gb as EXT 3 w/ 2gb as Linux-Swap. Keeping the other drives as additional storage.
From what I've learned, you could format the IDE drives as FAT 32 and they would be accessed by linux or windows.
I, too, prefer my OS's on different drives but that 500 gb drive is plenty of room for both saving the other drives for backup or storage for stuff you don't want to lose if the SATA dies.

                                                         Good Luck.

---

### Post by Tiger-Smith on 2007-09-04
Always install any Windows Os first otherwise it will overwrite Grub in the mbr and will replace it with ntldr, simply put sure youll get a fully functioning Windows but your linux partition will become unsuable untill you rewrite the mbr with grub boot tables. There are workarounds such as reinstalling grub but it isnt recommended as it can bugger both oses.

---

### Post by toolfreakuna on 2007-09-04
Okay. =(

Well, I will reformat the SATA to take the WinXP installation, then...

Do I partition it after running the LiveCD, or do I need to partition it before that? And can I do it automatically, or do I need to do it manually?

Thanks for the many replies, by the way.

---

### Post by rsambuca on 2007-09-04
If you are going to start fresh, then always partition first.  This way, you don't have to worry about any filesystem corruption occuring from partitioning a pre-exisiting OS.

Personally, though, I see no reason to wipe everything in your case.

---

### Post by toolfreakuna on 2007-09-04
Okay... so how would I go about doing this? Sorry, I'm pretty new at this partitioning stuff.

---

