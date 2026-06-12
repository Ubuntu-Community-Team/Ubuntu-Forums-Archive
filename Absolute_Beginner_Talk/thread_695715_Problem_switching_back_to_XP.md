---
title: "Problem switching back to XP"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by walden50 on 2008-02-13
Hi guys - hope you can help.

Installed Ubuntu on my laptop, and ended up having some problems with the wireless card drivers.  I'm sure I can fix it eventually, but right now I need windows back just for a few days.

I used GParted to delete all partitions, and reformat the entire drive as one NTFS partition.

Then I try booting off the WIN XP CD (yes, boot order is good) and it's like it doesn't even see the disc.

Eventually it ends up with:

GRUB loading, please wait...
Error 17.

Please help!!  Thanks!

---

### Post by hyper_ch on 2008-02-13
is the disc ok or is it scratched?

Is the disc bootable (did you try on another computer)?

---

### Post by RussellGee on 2008-02-13
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945) 

That should help you.:wink:

Russell

---

### Post by walden50 on 2008-02-13
The disc is ok, and I've tried two separate XP copies, with same result for each.

---

### Post by walden50 on 2008-02-13
> **RussellGee said:**
> [http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945) 

That should help you.:wink:

Russell

My BIOS is detecting the HD just fine, and does not allow me to change HD settings.  This is in the "PheonixBIOS Setup Utility"

I saw something about I have to remove grub first - but can't find it again.  Should i reinstall ubuntu since i already deleted the partition?

---

### Post by melojo on 2008-02-13
boot from the xp cd cdrom support and type fixmbr, here is a link.
[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm)

---

