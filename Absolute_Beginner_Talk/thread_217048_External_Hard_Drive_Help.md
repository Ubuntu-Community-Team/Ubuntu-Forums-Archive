---
title: "External Hard Drive Help"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Gonzo_PhD on 2006-07-16
I have an external hard drive, and was wondering how I can view it in Ubuntu 6.06? Is it supposed to pop automatically like Windows?

Thanks.

---

### Post by crispy_420 on 2006-07-16
Did you already plug it in and nothing came up?

And what format is it? (FAT32, NTFS, etc.)

If your drive is formated as NTFS you may be out of luck unless you do a reformat. How you format it will then depend on your needs. There is read support for NTFS but if you need to write, the support if bad at best. If you write to NTFS you may just end up losing data.

Will you need support for another OS besides linux? (OSX, Windows, etc.)
What size files do you plan on storing? (over 4GB)

These are some questions you will have to ask yourself. If you don't plan on sharing files you can format to ext3 or another native linux format which doesn't have a size restriction for files or even one for size of drive. But you won't be able to share your files with windows without installing support on those systems which may not be an option (schools, work, etc.). But then if you go with something like FAT32 you can share at a cost. You won't be able to have files larger than 4GB (distro downloads, DVD iso's, etc.). Also I think there is a restriction on the size of FAT32 partitions. And there are others I don't have a use for so I can't comment on, mainly the MacOS ones like HFS+.

I personally have a secodary drive formatted  50/50 FAT32 and NTFS. Since I have swappable drives for the OS I wanted to be able to share certain files across any OS installed (Windows XP, WIndows 2000, Ubuntu, etc.). But the NTFS portion is reserved for Windows only.

Hope this helps or did I go over board. But the main point is what will you need this drive for?

---

### Post by Uncle Spellbinder on 2006-07-16
I've had no problems viewing and accessing music and files on both of my Maxtor external drives (NFTS). I've even imported music to *Listen* and *Rhythmbox* from my external drive.

---

### Post by Gonzo_PhD on 2006-07-16
I use it to store music. I think its NFTS because I use it with Windows XP. I don't need to write data on it, just read support. It is plugged in.

Thanks.

---

