---
title: "Multi Purpose Box"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Tri_X_Troll on 2006-11-16
With the recent release of edgy eft, I've been using windows less and less.

I'd like to kill my winblows partition, but I still use it for some select software and games. The linux partition is mostly being used for email, word processing, spreadsheets, and web surfing, and mp3s, streaming, movies, burning (most everything)

I have a need and a want for both operating systems. Because of the manner in which I work on some projects, I'd like my "home folder" equally accessible  from both operating systems. I'm thinking that I'm going to start over from scratch on the whole machine.

I have in front of me, two 80 gig Western digital hard drives, 2 gigs ddr, and an idea.

HD1
*40 gig windows partition (ntfs)
*40 gig linux partition (ext3)

HD2
*80 gig storage for music, movies, photos, and office documents.

Now, my query. I want to be able to both read and write to HD2 from both operating systems, how should I set it up? I've heard that writing to an NTFS partition from linux is still unstable, what would be a stable filesytem?

---

### Post by aidanr on 2006-11-16
fat32, only drawback is the 4gig filesize limit which prevents storing dvd backup iso's or large uncompressed video etc

---

### Post by Tri_X_Troll on 2006-11-16
well poo. I'd completely forgotten about that 4 gig limit. perhaps a differnt  plan of action needs to be taken

---

### Post by 3rdalbum on 2006-11-16
Format the HD2 as Ext2, then install the Ext2 driver for Windows.

Or you could format the HD2 as NTFS and use the beta NTFS driver for Linux - just make sure the drive doesn't get too fragmented, and keep a backup of everything important.

---

