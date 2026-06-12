---
title: "Partition error during Install"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by drawab on 2006-09-21
Hi,

Well I'm simply itching to install Ubuntu v 6.06.1 on my computer. specs Toshiba Satellite P20-S103, Intel P4-Hyper-Threading & Nvida 5200, 60GB HD.

I am able to run the Live CD perfectly, when I start the installer it get stuck in the partition area, I have repeated this a few times and each time it hangs up giving an error with automatic installation and also Gparted installation "Unable to create enough space for Installation".  My HD plan is as follows.  Just recently I cleaned up the HD to have a decent 18GB free of which i will dedicate 10GB to Ubuntu (which should include the Swap also).  This partition error also creates some problems on the disk itself as chkdisk scans the drive for NTFS table but is able to locate and boot windows.

Would appreciate any help, i read on the forum that it could be possible to use partition magic to re size Windows partition and then use Ubuntu to fix things up in the unallocated space. *(I could just be blabbering hot air ;) *

Open to ideas and suggestions, I have run a full defragmentation of the drive so things seem to be OK there.

---

### Post by davmac on 2006-09-22
I've not come across this before. I'd tackle this by downloading and burning a copy of The Ultimate Boot CD ([http://www.ultimatebootcd.com/)](http://www.ultimatebootcd.com/)).

When you boot up with this you can press F2 for the filesystem tools and then (from memory) F1 for Ranish Partition Manager. Using this to resize partitions is fairly self explanatory, but shout up if you need further help.

As with anything of this type, make sure you've got a full backup of everything you care about.

Regards,

Dave Mac

---

