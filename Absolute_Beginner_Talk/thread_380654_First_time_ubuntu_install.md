---
title: "First time ubuntu install"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by scifi1983 on 2007-03-09
Hello, i just downloaded ubuntu desktop 6.10. I have a 80gb ide hdd, a 120gb ide hdd and a 160gb sata hdd. I boot up with the ubuntu disk (burnt in winxp @ 4x onto a cd-rw). 

The 80gb has a 10gb partition in fat32. the rest is ntfs (ie 70gb,120gb & 160gb.)

 When i try to install i get "Resize ide1 master partition #5 hda5 and use free space". I click next and the install hangs. 

what am i doing wrong?? any advise will be muchly appreciated.:confused:

---

### Post by mikewhatever on 2007-03-09
Is the partition you are tying to resize almost full? Have you defragmented it?

---

### Post by scifi1983 on 2007-03-09
Thanks for the reply.
The partition is empty. I booted with my xp disk and deleted my original windows partition (ie c:\)
and created a new fat32 partition. i quit the setup and booted with ubuntu. the drive has not been defragmented. How would i defrag a drive in ubuntu if it is at all possible?? I really need help with this. Im going nuts trying to install this. if i cant im going back to mirco$hite windows.

---

### Post by ZeroXR on 2007-03-09
mike probably meant if you have defragged the drive from Windows XP.

Do that first and it should resolve your problems.

---

### Post by mikewhatever on 2007-03-10
I remember having a problem resizing my Windows partition due to some inconsistensy. I had to run CHKDSK check from Windows to get it solved. It is not quite your case, but may help. Do you still have a Windows OS installed, or was the one you deleted the only OS. I think you can run that check from GParted live cd. Not sure if Ubuntu installer has the option. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Edit: How about deleting the entire partition and creating the Linux ones of desired size with the live cd.

---

