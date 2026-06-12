---
title: "Transferring Data over to new hard drive"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by uncle_pete on 2007-09-10
I apologize for this sortof being a common question, but I'm having a hard time figuring out exactly what is the best course of action. 
My current setup is a desktop, with two hard drives, 1-40gb IDE set as master with original windows xp home, and 1-20gb IDE set as slave installed with 7.04 ubuntu using the graphical installer for the entire disc. 
Currently they are running nicely as dual boot, I'm mostly using the ubuntu, but want to leave the xp as is due to some software I need to use once in a while. I just picked up a 320 gb SATA hard drive. Ideally I would like to transfer the ubuntu installation to the new hard drive and leave a significant partition that is accessible through both windows and ubuntu for storage of media and documents and such. I could deal with completely reinstalling ubuntu and losing my settings, but I would prefer not to, if it would be easy to transfer ubuntu and create the necessary partitions. From my limited experience it seems like it might be easiest for me to simply take out the old 20 gb hard drive with the ubuntu installation, reinstall ubuntu from the live cd onto the new hard drive and make the neccessary partitions during the installation. Any recommendations would be appreciated. Thanks

---

### Post by BrendanM on 2007-09-11
You could just intall Ubuntu on the new hard drive and then copy over your /home folder.

In terms of making a partion that's accessible to both Linux and Windows, there's basically three ways to do this:

Option 1) Make the partition with the FAT32 file system. Both Linux and Windows can read FAT32 partitions natively. There are some disadvantages with this option, the biggest drawbacks being a 4 gig file size limit and fragmentation issues.

Option 2) Make the partition NTFS and install NTFS-3G so you can write to the partition from Linux.

Option 3) Make the partition ext3 and install the ext2fs driver in Windows so Windows can read/write the partition. Windows will NOT respect Linux file permissions.

Good luck.

---

### Post by bodhi.zazen on 2007-09-11
Copying over /home may not be so straightforward :)

You can "copy and paste" your ubuntu partition with gparted. To make it bootable you will then need to edit /etc/fstab and /boot/grub/menu.lst to reflect the changes you made.

See this thread for guidance :

[http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)

That like will review the changes you will need to make (you will have to user your partitions)

HTH

---

