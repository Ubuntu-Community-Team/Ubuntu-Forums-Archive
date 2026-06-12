---
title: "Portable hard drive mac/ubuntu"
date: 2015-08-24
forum: Apple Hardware Users
---

### Post by DiggerDigwillow on 2015-08-24
I'm looking for advice about portable hard drives. I am taking graphic design classes where we use mac computers and software, and it is highly recomended that I use a portable hard drive to back up my files for class rather than just using a flash drive. 

I am familiar with saving files on a flash drive, and I know that I can view and use .psd files in gimp. I am not sure about whether I would be able to view/use files saved on a mac formated hard drive with Ubuntu (14.04)

If there is any helpful info out there it would be apprciated...I did some google searching, but wasn't finding much explained at a level I could understand...

---

### Post by VChief on 2015-08-24
Well, I do believe that if it's formatted in FAT32, you should be able to use it in both Mac and Linux without an issue.

---

### Post by nerdtron on 2015-08-24
If you are a graphic designer some big project files can reach 4GB (which is the limit of FAT32). I think Macs can also read/write NTFS files which is also supported in Linux.

---

### Post by sandyd on 2015-08-24
> **nerdtron said:**
> If you are a graphic designer some big project files can reach 4GB (which is the limit of FAT32). I think Macs can also read/write NTFS files which is also supported in Linux.

Read only by default.
Write will require something like [Tuxera NTFS]("http://www.tuxera.com/products/tuxera-ntfs-for-mac/")* or [Paragon NTFS for Mac]("https://www.paragon-software.com/home/ntfs-mac/")*

* Disclaimer, not an endorsement for either product, I have just used both at one time or another, and they work for my purposes.

---

### Post by VChief on 2015-08-25
Ah. I hadn't considered the graphic designer angle. I tend to limit partitioning to NTFS just because of the crummy write support (without additional software which sandyd has posted about).

---

### Post by howefield on 2015-08-26
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by crystalocean on 2015-08-27
Try looking into hfsprogs. It should allow you to write/read to/from hfs+ portable hard drives.

---

### Post by JohnAtilano on 2015-08-29
Why not format the drive as exFAT? You can read/write from both systems and it doesn't have the 4GB file size limit that FAT32 does.

---

