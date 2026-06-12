---
title: "How would you: partition a HD so you can install another OS on a PC with Ubuntu?"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-03-02
[B]Would any of you please tell me how you would partition the hard-drive on a desktop computer, which has a pre-installation of Ubuntu? I would like to use a custom version of Windows XP (made by the "NLite OS team").

Thanks for reading this message. 

I appreciate anyone, who is willing to help us solve this problem by giving us an answer in a step-by-step instructional format.[/B]

---

### Post by neurostu on 2008-03-02
I would have 4 partitions.

1 for Ubuntu
1 for Swap
1 for XP
1 for File Sharing across the two OSes

The reason for the 4th parition is XP can freak out if linux starts messing with its files.   It really isn't a problem to read a XP HDD, writing; however, can cause the problem.

---

### Post by ahuman on 2008-03-02
[B]Thanks for helping me. I appreciate your kindness. Would you or anyone else  please tell me step-by-step instructions about how to completely wipe-out my pre-installation of Ubuntu so I can get Windows XP on my computer?

Afterwards, I would like to re-install Ubuntu, so I can set up the "Dual-Boot" system on my computer (which is a Dell Inspiron 531s with AMD64).[/B]

---

### Post by neurostu on 2008-03-02
How would I partition it?

I would use GParted,  you can download it from SourceForge. 
Select the primary partition, then resize it. Then create two new partitions from the remaining space using gparted.

The Windows XP partition has to be on the first partition.  

Also when you install XP it will write over your MBR (master boot record) so you will have to reinstall grub.  That isn't a big issue, searching for "Install XP after Ubuntu" in google will bring up a lot of hits on how to fix grub.

---

### Post by neurostu on 2008-03-02
Ohhh........ You want to wipe Ubuntu first? 

That is really easy. (and you won't need to mess with partitions)

Put in the XP install cd. Let it install as normal.

Put in the Ubuntu Live cd, boot then click install, when it comes to partitioning tell it to split the drive (which it will do) (I think it is the GUIDED option??). 

Then let it run.


If you want an exact step by step there are tons on google. Just search for it.
Also check this post:[http://ubuntuforums.org/showthread.php?t=398255](http://ubuntuforums.org/showthread.php?t=398255)

---

### Post by raydeen on 2008-03-02
The only other thing to mention is that if you choose to have a partition for sharing files between the systems, it would be a good idea to make it a FAT 32 partition. Everything can read/write to that and there won't be any permission problems to worry about.

---

### Post by ahuman on 2008-03-02
**[COLOR="Green"]Thanks to both of you. I appreciate all of your help, you 2 have provided. Be safe & take care. May I add _both of you_ to my list of friends?[/COLOR]**

---

### Post by neurostu on 2008-03-02
Sure, that fine with me.

---

