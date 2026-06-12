---
title: "/media"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by bootyblind on 2008-04-09
Hi all,

I can't seem to find this anywhere - though i don't know exactly how to look for this one!

I have just installed Ubuntu (Hardy) onto my PC.  It was running fine with a addtion to my fstab file to mount my NTFS partition.

My dilemma appears to be that now everytime I start Ubuntu it adds another entry into the /media folder.

What do i mean?

I have a NTFS partition that is called Sydney - but everytime I load Ubuntu it will re-mount as Sydney_, and then Sydney__, Sydney___ and so on and so forth.

It happens with my iPod as well.

Now i have my Music and torrents for Azureus on this HDD and the programs are obviously reporting 'broken' links.

I have tried removing the mount instructions from fstab - still when the system recognises it (shows in Places automatically) it adds the '_' to the end of the previous session.  How do I stop this and keep the exact same name each time?

---

### Post by philinux on 2008-04-09
I'd read all the posts before attempting a fix.

[http://ubuntuforums.org/showthread.php?t=744469](http://ubuntuforums.org/showthread.php?t=744469)

---

### Post by vanadium on 2008-04-09
These are all removable drives? Then disconnect the drives, remove all entries from fstab, delete the mount points under /media. When plugging in the drive, it will mount automatically. Here [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive) you can find how to control the name of the mount point.

---

