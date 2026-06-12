---
title: "Ext2ifs not working well for me - other options?"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by trishacupra on 2007-11-21
Hi,

I've had really mixed results with using ext2ifs to be able to read/write ext3 partitions in Windows XP. Yes, this is a XP problem, not a Ubuntu problem, at heart. So, if there are any dual booters out there like me, please help me out if you can.

The problem I have is that I can install ext2ifs fine, I can assign drive letters fine, and then it may work for a little while just fine. Then, suddenly, I go to My Computer one day and the partitions are showing up, but if I click on them, XP asks me if I want to format the partition. Well, *heck no*, I don't want to wipe my partition. So XP thinks it's unformatted and naturally I can't access my files.

I do have a FAT32 partition set up to make sharing files easier, but it's a pain in the butt to have to move anything I might need onto it before booting up Windows.

ext2ifs seems to have had no active development for years. What else is out there that I could use? Or, does someone know a fix for my bug?

I think maybe have an external hard drive with a lot of partitions may be contributing to the problem, but I just want to use my internal partitions, mostly. When I try installing ext2ifs with the external drive unplugged, I still get the bug after a while.

Thanks very much,
Trisha

---

### Post by p_quarles on 2007-11-21
I'm not aware of any alternatives for reading ext2/3 filesystems from within Windows. 

Anyway, I think you have a couple options that could work. The first is to just start pointing your apps to save your files on the FAT32 partition instead of the /home directory. You could also change it to an NTFS partition (more efficient) and do the same thing. 

The other option: if you have an old computer lying around (or if you can pick one up used for cheap), you could set it up as a Samba server. That would allow you to create a shared network folder that would perform very well with both operating systems. I think this is the best option, but it depends on your owning/buying some hardware.

---

