---
title: "Access to saved Windows XP"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by micfreedom on 2007-05-07
Dear ubuntu,
I have installed a dual-boot of Ubuntu on my computer. I have saved previously "my  documents" on an external hard drive.
Ubuntu works fine.
Problems:  :( 
1. When I reboot, the booting process goes so rapidly that I cannot get into the CMOS, even when I press "Delete" on restart. The machine by-passes my command straight into Ubuntu.
The reason why I would like to change the settings is that i cannot see Windows XP any more, and i'd like to see my past work in it.( I also would like to transfer the files and addresses from Outlook Express)

2. I cannot access the saved "windows XP" on my external hard drive. I see it, but when I click to open it, it says "You are not the owner, you cannot change the permissions" How can I retrieve the data that is found there. I have essays, letters as well as photos, and my email addresses.
I'd like to make ubuntu work. I am sort of charmed by it, although it is quite a learning curve with learning to use the terminal with sudo!

---

### Post by fakie_flip on 2007-05-07
push alt f2 in ubuntu and type gksu nautilus
then browse to windows xp and it shouldnt give you an error about permissions this time.
are you sure you installed a dual boot and not overwrote windows xp? you can push escape during boot when you see grub to get the menu.

---

### Post by Mr.Beast on 2007-05-07
> **micfreedom said:**
> Dear ubuntu,
I have installed a dual-boot of Ubuntu on my computer. I have saved previously "my  documents" on an external hard drive.
Ubuntu works fine.
Problems:  :( 
1. When I reboot, the booting process goes so rapidly that I cannot get into the CMOS, even when I press "Delete" on restart. The machine by-passes my command straight into Ubuntu.
The reason why I would like to change the settings is that i cannot see Windows XP any more, and i'd like to see my past work in it.( I also would like to transfer the files and addresses from Outlook Express)

2. I cannot access the saved "windows XP" on my external hard drive. I see it, but when I click to open it, it says "You are not the owner, you cannot change the permissions" How can I retrieve the data that is found there. I have essays, letters as well as photos, and my email addresses.
I'd like to make ubuntu work. I am sort of charmed by it, although it is quite a learning curve with learning to use the terminal with sudo!

The external hard drive should allow you read only permissions, so I would suggest at least copying the files over to your /home area on your machine.  This should give you read write permissions. 
You can copy the files in the same way, that is highlight the ones you want, and press CTRL C, then click, the PLACES, and then select Home folde, and put the files in there.

hope this helps.


hope that this helps

---

### Post by micfreedom on 2007-05-07
> **fakie_flip said:**
> push alt f2 in ubuntu and type gksu nautilus
then browse to windows xp and it shouldnt give you an error about permissions this time.
are you sure you installed a dual boot and not overwrote windows xp? you can push escape during boot when you see grub to get the menu.

When I installed the disk, I did the automatic partioning!
I did as you said , when i clicked run, i had "The location or file could not be found."
I said run with file, so I did, I could not see anything there!:( :(

---

### Post by fakie_flip on 2007-05-07
open a terminal and put this in. i just tried it, and it works for me.

gksu nautilus

---

### Post by micfreedom on 2007-05-07
When I copied gksu nautilus
it went to the process and opened a window with root, destop and files. Nothing is in the desktop, root I dare not see what's in this, and files there are, but not Windows XP or any documents that I saved on the external hard drive. Do you think it's all erased???

I have a CD with a bsckup of my files on it. Do you think i cold use this to copy my files into Ubuntu.

Sorry, I am a bit concerned to say the least!

---

### Post by lxop on 2007-05-16
I daresay if you installed Ubuntu with automatic partitioning, you may well have overwritten your Windows partition. Go to Places, Computer, and this should show all your partitions/HDDs. If you're still uncertain, check the sizes of each partition, and compare the total to how big your HDD is.

---

### Post by micfreedom on 2007-05-17
> **lxop said:**
> I daresay if you installed Ubuntu with automatic partitioning, you may well have overwritten your Windows partition. Go to Places, Computer, and this should show all your partitions/HDDs. If you're still uncertain, check the sizes of each partition, and compare the total to how big your HDD is.

Thank you,
I saw partitions, but on the external hard drive there was nothing in the saved partition that was supposed to contain Microsoft stuff of mine!
I tried the External Hard Drive on my wife's computer, but EHD would not be recognized.
I think I did a bad job:
1. In saving
2. in trusting  My Book Essential, as an external hard drive. I did put this question to Western Digital. They advised me to replavce the E.H.D. I just bought!!!
I will do so, but I will explore which external hard drive IS compatible both with Windows XP and Linux.
This is a bad experience for me --- too trusting.

I found that Bytestor memory stick are more reliable. I trusted some older data to it and found I could use it again safely without corruption.
Thank you so much.
I'll have to rethink abou Linux and learning a little more on how to operate it. it is quite a learning curve!
(I'll post my warning about My Book Essential in a new post)

---

### Post by ugm6hr on 2007-05-17
Sorry to hear of your problems.  If the "My Book" exteral HD doesn't work on your wife's (presumably Windows) computer, it is likely to be a problem with your "My Book" rather than a compatibility issue.  I have a Western Digital Passport (2.5" external USB hard drive) which works fine with Linux (inc Ubuntu).  In fact, unlike many other HDs, it is preformated in FAT32 (rather than NTFS) to allow compatibility with all Windows, Macs and Linux.  The other thought I had is: does Ubuntu automatically recognise NTFS partitions?  If not, and your HD is NTFS, that might explain why you can't access it.  Might be worth checking with GParted to see what format it is.  And ensure that NTFS read/write is installed.

---

