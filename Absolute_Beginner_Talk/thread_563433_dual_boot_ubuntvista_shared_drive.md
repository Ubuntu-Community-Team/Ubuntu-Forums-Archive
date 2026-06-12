---
title: "dual boot ubunt/vista shared drive"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by morior on 2007-09-30
Is it possible to have a dual boot system that shares a 500 raid mirror drive? if it is possible how would I set it up and I know a few things about ubuntu, but please don't assume I know something simple just yet.  spell it out for me.

---

### Post by amonrath on 2007-09-30
> **morior said:**
> Is it possible to have a dual boot system that shares a 500 raid mirror drive? if it is possible how would I set it up and I know a few things about ubuntu, but please don't assume I know something simple just yet.  spell it out for me.

um i got xp/vista ultimate/and ubuntu all crammed into an 80 gig ide deskstar it runs fine except every now and then my feisty won't runup properly but ive found that if you i reset with ctrl/alt/delete when it tried to tell me it was failing  it reloaded cleanly probaly due to the previous os's crap still residual still leftover in the system, my old girl has a initio sata raid with two sata's hookdup but i have'ntkickd up the mirror as i need the space

---

### Post by Golyadkin on 2007-09-30
It will work perfectly, as long as you use a filesystem that can be read / written by both operating systems. This can be NTFS for instance.

---

### Post by morior on 2007-09-30
> **Golyadkin said:**
> It will work perfectly, as long as you use a filesystem that can be read / written by both operating systems. This can be NTFS for instance.

what are the file systems I can use with Ubuntu and vista?

---

### Post by Golyadkin on 2007-09-30
Well, Vista is so crippled it can read and write pretty much only FAT, FAT32, SMB and NTFS.
Linux (and thus Ubuntu) can work with over 70 filesystems, but including FAT, FAT32, SMB and NTFS. So the choice is easy.

---

### Post by rsambuca on 2007-09-30
> **morior said:**
> what are the file systems I can use with Ubuntu and vista?

Since nobody wants to answer your question directly, I'll jump in.  While there are a few more that can be read by both systems, the three best choices are FAT32, ntfs, and ext2/3.

FAT32 is read/write by both systems natively, but it is really not a good filesystem, and thus I can't recommend it at all.

ntfs is MS's fileformat.  Ubuntu can read/write to ntfs with the ntfs-3g driver, and can be automatically set up for you with the ntfs-config.

ext3 is probably the best filesystem of the three.  Unless you have very unusual files, you really don't have to ever defragment this system as it is automatically defragged with use.  It is the system I would recommend.  You can use ext3 with vista using the [fs-driver]("http://www.fs-driver.org/") for Windows.  To install in Vista, just make sure you select the XP compatibility mode.

---

### Post by morior on 2007-10-02
> **rsambuca said:**
> Since nobody wants to answer your question directly, I'll jump in.  While there are a few more that can be read by both systems, the three best choices are FAT32, ntfs, and ext2/3.

FAT32 is read/write by both systems natively, but it is really not a good filesystem, and thus I can't recommend it at all.

ntfs is MS's fileformat.  Ubuntu can read/write to ntfs with the ntfs-3g driver, and can be automatically set up for you with the ntfs-config.

ext3 is probably the best filesystem of the three.  Unless you have very unusual files, you really don't have to ever defragment this system as it is automatically defragged with use.  It is the system I would recommend.  You can use ext3 with vista using the [fs-driver]("http://www.fs-driver.org/") for Windows.  To install in Vista, just make sure you select the XP compatibility mode.

Thats sounds great, I'm waiting for the drives to test it out on, but it sounds perfect.  Now if I want to share out folders from the ext3 drive will I have to install fs-driver on all the windows pc's?  Can I share it out through ubuntu and vista?  example being I want to be able to access my documents and the home folder from each one, but everything from those folders will be stored on the ext3 drive.

---

### Post by Ekkusu on 2007-10-02
That was what I wanted to do so I didn't have to move everything. Is that possible: sharing files between Windows and Ubuntu?

---

### Post by rapsball4 on 2007-10-21
I'm looking to set up the same thing.  I have a 250 GB drive that I'd like to split in half between Vista and Ubuntu Gutsy (both amd64), and then a 500 GB that I'd like for data to be shared - all my movies, music, documents, etc.  Will the ext3 setup you mentioned work with my 64-bit Vista or will it only work with 32-bit?  If ext3 is a better option, I'd like to go with it, but if its impossible or nearly impossible to set up and the NTFS way is easier, I'll just take that.  What do you recommend?

---

