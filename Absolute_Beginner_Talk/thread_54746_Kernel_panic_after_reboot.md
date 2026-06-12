---
title: "Kernel panic after reboot?"
date: 2005-08-05
forum: Absolute Beginner Talk
---

### Post by AlexDe on 2005-08-05
I just rebooted like I have been for the past month no updates within the past week.. and out of nowhere I get a kernel panic.

********ERROR MESSAGE********

/sbin/init: 428: cannot open dev/console: No such file
Kernel panic - not syncing: Attempted to kill init!

******END OF ERROR MESSAGE****



Yes i've search google and the forums, plenty of posts.. none seem to help me (of course im new so maybe some arn't really helping me?)

Im using lilo, not grub. 

Thanks, and sorry for the repetitive post

---

### Post by Rapaport on 2005-08-05
i believe this is a common error as I am having the same issue and have discovered many, many posts on this forum and others describing this specific error. 

Search in the Ubuntu forums for (pivot_root) and also install external USB and similar phrases. You'll find threads addressing this issue. Unfortunately, I still have not been able to resolve the issue. In fact, I've had to run a fixmbr windows rescue 3 times after GRUB corrupted. Keep at it, and when you find instructions to install into USB, play around. That's all us newbs can do, I suppose.

---

### Post by AlexDe on 2005-08-06
Ya i've seen it all, just not really that can help me "specifically" ... probably because Im not as knowledgeable as some, but i'll look some more thanks!

---

### Post by AlexDe on 2005-08-06
I can't seem to figure out what caused it and or how to fix it... any ideas.. sorry for the **BUMP** but im exausted from looking.. thx.

---

### Post by Rapaport on 2005-08-07
I'm having the same issue. 
Are you trying to boot from a USB hard drive? 

It seems to me that a USB hard drive "can" boot Linux, but doesn't like to boot linux. Linux has issues identifying the root partition on the USB, I think. So I guess if you're a newb, like me, its difficult to set the configuration right. I've tried to mess with the initrd.img but it hasn't worked. I read that trying to get your USB to boot from the initrd is risky and unreliable.

Its a shame, Linux could probably break out as an alternative OS if people could run a completely indepedent Linux atmosphere from an external HD w/o having to mess with their MBR or partitioning on the main HD. I know this can be done but the errors I'm coming across, as a newb, I cannot solve.

Sorry, I can't help more. I need help solving this error issue too. I've given up trying to install Linux on my external HD. At this point, I'm looking for a cheap notebook on ebay to mess with.

---

### Post by AlexDe on 2005-08-07
Nope normal hd.. been booting w/ it for 1-2 months now.. and out of the blue just did it :\

---

### Post by Koba on 2005-08-29
so have you found the solution for this problem yet orr...? because i have the EXACT same message on my boot up of Ubuntu, and i can't seem to find out why :\

---

### Post by joaovicente on 2005-09-01
[QUOTE=Koba]so have you found the solution for this problem yet orr...? because i have the EXACT same message on my boot up of Ubuntu, and i can't seem to find out why :\[/QUOTE]
 I'm having the same problem. I'm using a normal HD installation of Ubuntu Hoary 5.04 with grub. This problem began after an automatic update. I can't boot Ubuntu anymore.

I have some partions, the mainly are:

.hda0 - WindowsXP   ntfs (dual boot)
...
.hda4- /boot (boot)   ext3
.hda5: / (root)           jfs
...

Any help would be greatly appreciated.

João Vicente

---

