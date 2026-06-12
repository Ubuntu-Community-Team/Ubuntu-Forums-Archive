---
title: "First time dual-boot HELP"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by TrueN00b on 2006-12-07
OK I need a straight forward howto to dual-boot my laptop.

windows xp is on and i have two partitions:  one is ntfs 60gb and the other is a 20 gb recovery partition that was on when i bought this laptop.

defragmented a lot but i just need a all in one howto for the most recent ver of ubuntu.

---

### Post by Spin Doctor on 2006-12-07
Check out this how-to that I used to create a dual boot XP / Edgy system. Works like a charm for me atleast.

[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=1](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=1)

---

### Post by carverj on 2006-12-07
This post --> [http://www.ubuntuforums.org/showthread.php?t=313772&highlight=dapper+xp+dual](http://www.ubuntuforums.org/showthread.php?t=313772&highlight=dapper+xp+dual)
may give you some partitioning advice !

Ensure that XP is installed to the first partition as Windows is very unfriendly. On my primary drive (very similar setup on my secondary drive by
the way), I installed XP first on an empty disk. then I insert the latest Linux OS and use its partitioner to divide the rest of the disk into the various ext3 and swap partitions that work for me. 
  Hope this is helpful

______________
:)  and the whole world :) 's with you !!

---

### Post by Spin Doctor on 2006-12-07
Another good read when it comes to planning your partions for a dualboot system:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by AndyCooll on 2006-12-07
I'm sure the links provided are fine. However, the link relating to dual-booting that is most often quoted on these forums is the one in my signature. Try that and you won't go wrong.

:cool:

---

### Post by TrueN00b on 2006-12-08
What about step-by-step guides?

i jus put gparted, systemrescuecd, and ubuntu on seperate dvd's (the only i have) and need to look around to move those 'unmovable' files on my hdd.

---

### Post by gn2 on 2006-12-09
If Windows Disk Defragmenter shows you have files where you want blank space to cbe for creating a Linux partition, and no amount of de-fragging will shift them along to the left.....

My advice under these circumstances is to get hold of a copy of Partition Magic which will resize the partition down, and move the files along. If you can't borrow a copy, club together with some friends, and it needn't cost too much...?
It is well worth the price if you need a good partitioning utility for Windows.

Re-size the Windows partition down and leave free space to install to, then create partitions with the Ubuntu installer as part of the install process for Ubuntu.

Make sure all data you need to keep is backed up to removable media first though.

And read up on Grub editing.

Or buy a second hard drive and try this: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by TrueN00b on 2006-12-09
Haven't read anything about grub but atleast I do know about it, so I'll read more on that.

Could anyone list the programs that I would need for the whole process just to make sure I have the correct ones.  I plan on taking what I have learned from this expierence and making a complete n00b-friendly step-by-step howto once I am done.

---

### Post by Paul133 on 2006-12-09
Andy, the guide you posted is only for the alternate install, not the grpahical install. And grub is a menu that loads right after BIOS that allows you to choose if you wasnt to boot XP, Ubuntu, or Ubuntu "safe" mode (for lack of a better word.

And, I think all you need is the ISO to install, no other programs (at least, I didn't need any others when I installed the server edition).

---

