---
title: "Replacing 64bit with 32bit"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by Twizzle on 2006-04-11
I am very new to Linux in any form, and installed Ubuntu yesterday for the first time. I have an amd 64 cpu and so blindly downloaded and burnt that version to CD and installed.
So far so good, and I have a system that runs and can boot back to Windows if needed :D 
I have run into a few little problems though and I am guessing that it is to do with the 64bit operating system and 32 bit programs. I have read enough of the posts to know that I can find workarounds and tweaks to enable them but as I am such a newbie I was thinking that I should stick to the basics and learn how it works before tweaking!
I now have the 32bit version ready to install. Can I just pop it in the CD drive and away I go with a fresh install over the top of the 64bit version, or is it advisable (and possible) to do a complete uninstall and then start from scratch?
I want to keep my XP on a seperate partition intact and acessable, so I don't really want to be formatting whole drives.

---

### Post by Sutekh on 2006-04-11
Nope its easiest to use the 32bit installation CD to format over the 64bit partitions and then install.

Just boot the installation CD, and choose to manually partition your discs.  

At this point no changes are to be made.  

Make sure you choose the partition that contains the 64bit installation and select it.  

In the options, choose to format it and then choose the appropriate mount point.  

If, when you installed the 64bit version you only made one partition, it would have been /  So for the 32bit installation make sure that the partition is mounted to / when you format it.


Hope that's clear.

---

