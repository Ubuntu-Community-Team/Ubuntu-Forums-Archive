---
title: "FAT32 data/share partition: data/filesystem integrity concern warranted?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by 5-HT on 2006-06-09
The time has unfortunately come: I will soon be needing to dual-boot with Windows.
I'm planning on creating a FAT32 partition for my Windows data (~/ equivalent) and to share with Ubuntu. 

I'm just wondering if I should be concerned that FAT32 is not a journaled filesystem, as data integrity is very important for the work I'll be needing to do in Windows and share with Ubuntu (I will of course be making appropriate backups).

An alternative would be to store my Windows data on a separate NTFS partition and create a FAT32 partition just for ferrying files between the two operating systems. However, I'm reluctant to do this as disk space is quite limited for me.

I'm wondering if anyone may be willing to share some recommendations (apart from giving Windows ext support)?
Thanks for any input!

---

### Post by Solver on 2006-06-09
Personally, I transfer files between Windows and Ubuntu without a FAT partition. XP stays on NTFS, Ubuntu on ext3. Linux reads NTFS very well, and under Windows, I'm using an excellent tool called Explore2FS - it can take files from your ext2/ext3 partition and copy them to the Windows drive. Maybe that's suitable for you?

Explore2FS:

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

---

### Post by MaximB on 2006-06-09
why not ???
make the share partition ext3.
there is a program that makes windows read and write to it 
windows will see it as ext2 but in linux it would still be ext3
look for yourself :
[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by 5-HT on 2006-06-10
Thanks for the responses and the links. 
Have any of you ever had any corruption from writing to ext3 on Windows?

It's been a while since I've last had a Windows install. If I remember correctly, XP takes up just under 2 gigs. Does that sound about right?

Thanks again!

---

### Post by Solver on 2006-06-10
I personally don't write to ext3 from Windows. If I need to transfer files from XP to Linux, I copy them to the ext3 drive while in Linux.

XP takes around 1.5 gigs if I remember correctly... then again, that's only the OS itself. If you want to actually *do* anything, you need extra software. So in my experience, a minimal usable XP system hits 2 gigs.

By the way, if you do write to ext3 from Windows, I think it should be pretty safe. after all, ext3 (unlike NTFS) is an open-source system, hence there's no reason why the write driver should be poor quality. On the other hand, writing to NTFS from Linux is still unstable, sadly.

---

### Post by 5-HT on 2006-06-10
[quote=Solver]I personally don't write to ext3 from Windows. If I need to transfer files from XP to Linux, I copy them to the ext3 drive while in Linux.

XP takes around 1.5 gigs if I remember correctly... then again, that's only the OS itself. If you want to actually *do* anything, you need extra software. So in my experience, a minimal usable XP system hits 2 gigs.

By the way, if you do write to ext3 from Windows, I think it should be pretty safe. after all, ext3 (unlike NTFS) is an open-source system, hence there's no reason why the write driver should be poor quality. On the other hand, writing to NTFS from Linux is still unstable, sadly.[/quote] 
Thanks again. :)
The way you do it should work great for my purposes.

---

