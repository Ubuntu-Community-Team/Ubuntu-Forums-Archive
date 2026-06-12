---
title: "USB Drive, missing free space"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by ushills on 2007-03-28
Hi

I have a 4GB MMC that I can access using Ubuntu, however, I think I have caused it to lose space.

I deleted some files from it to make some room, however, the free space did not increase.  So I used it in my Pocket PC and deleted the trash folder.

Now in my Pocket PC it shows 520Mb free in Ubuntu 62Mb, I have tried deleting more files then using the "empty trash" option in Nautilis, however, the freespace never goes back to the true 520Mb.

What should I do, without refomatting the MMC.

Thanks

Ian

---

### Post by kinson on 2007-03-28
Open up your thumb drive using Nautilus(or whatever file manager), and make it show "hidden files". You'll see that there's a folder called something like ".Trash-<username>" which acts a bit like a recycle bin. Your previously "deleted" files should be within, just delete it from that folder, and your free space should be reclaimed.

Hope that helped.

Cheers,
Kinson :)

---

### Post by ushills on 2007-03-28
Hi that is my problem, I deleted the files outside of Ubuntu in WM5, my .trash folder is empty I can view it in XP & Ubuntu.  However, the free space is incorrect, it appears that Ubuntu is remembering the available free space, now I have a 4gb MMC with 3.2gb capacity.

---

