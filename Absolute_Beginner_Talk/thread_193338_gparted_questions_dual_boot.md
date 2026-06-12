---
title: "gparted questions dual boot"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by serendipity576 on 2006-06-09
I've been reading and have an idea of what to do, but can't figure out one thing.  Here's some history.  
      I initially upgraded from Breezy to Dapper but garbled it up enough screwing around so I burned an iso image and now I'm about to do a reinstall.  I have an XP partition(20GB), a 45GB partition NTFS, an ext3 partition that is 8GB which is where Ubuntu is now, and then a swap.  
     When I put in the Dapper install cd and I get to gparted, what steps do I take.  All I want to accomplish is erasing the ext3 partition and install Dapper over that.  However, I know you have to "mount" all of the partitions before finalizing all the changes and installing.  I have to admit I don't even know what "mount" means.  So when I get to that point, what do I put next to the windows partition so that it won't mess with it.  Also, I still want to dual boot of course, so where will the installer put GRUB, in the ext3 partition?  Thanks for any help.

clay

---

### Post by glotz on 2006-06-09
The installer will ask you where to install. Just select the 8GB partition and tell the install to erase it. If you're not making a separate boot partition, the grub will be on the 8GB disk.

---

### Post by serendipity576 on 2006-06-09
ok, well I read psychocats.net/windowstoubuntu and that helped, so I just put /windows for the mount point on windows and the only two boxes that were checked for reformatting were the swap and /  mount points.  The / one being where Ubuntu was already installed, so hopefully all goes well and I can still dual boot.....or this may crash and go down in glorious flames \\:D/ , who knows....lol.  What do you guys think?

---

### Post by glotz on 2006-06-09
I think your odds are good. However, if you do have mission critical data, it's always good to have backups (regardless of OS reinstalling...)

---

### Post by serendipity576 on 2006-06-10
Everything went well....whew!   I was all set for a meltdown mentally on that deal.  Thanks all.  :KS

---

