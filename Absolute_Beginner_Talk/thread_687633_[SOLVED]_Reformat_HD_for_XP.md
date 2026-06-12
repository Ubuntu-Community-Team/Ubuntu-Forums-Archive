---
title: "[SOLVED] Reformat HD for XP"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by sundance2007 on 2008-02-04
I have a hard drive formatted for Linux and I want to format it for XP but the windows tools I have used don't seem to be able to deal with the Linux partitions.

What should i use to delete the Linux partitions and format the whole drive to NTSF or FAT32?

Thanks

Steve

P.S. I realize this might be a better question for a Windows forum but I'll ask here as well.

---

### Post by cotcot on 2008-02-04
Erase them with gparted (gparted liveCD) or format them as FAT32.
If you reinstall XP it should recognise FAT32.

---

### Post by jan quark on 2008-02-04
I would use the gparted live Cd

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by nat6138 on 2008-02-04
Just delete the partitions, click Install or whatever, and it should come up with a dialog box saying format to NTFS.

---

### Post by bump_ on 2008-02-04
Try booting from your windows cd and deleting the Linux partitions. Then format the whole harddrive and windows should do it in NTFS

---

### Post by Pandemic187 on 2008-02-04
As others have said, this shouldn't be a problem. In fact, I've done exactly what you're trying to do before with no issues. All you need to do is boot from the XP CD (as has already been suggested) and edit the partitions that way. Once the XP partition manager starts, I believe the Linux partitions will appear as having "unknown" file systems. So all you have to do is delete the partitions with unknown file systems, create new partitions for XP, format them, and you should be good.

---

### Post by sundance2007 on 2008-02-04
Thanks for the help, Gparted worked great.:biggrin:

---

### Post by jan quark on 2008-02-04
great to hear

pls mark this thread as solved if you feel it is solved for you
use the thread tools at the top of the page

thank you

---

### Post by sundance2007 on 2008-02-04
> **jan quark said:**
> great to hear

pls mark this thread as solved if you feel it is solved for you
use the thread tools at the top of the page

thank you


How do you do that?  I see it now, thanks.

---

