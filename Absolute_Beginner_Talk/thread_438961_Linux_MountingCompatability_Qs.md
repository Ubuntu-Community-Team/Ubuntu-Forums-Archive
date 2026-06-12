---
title: "Linux Mounting/Compatability Qs"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Mutal1ty on 2007-05-10
First off, I have **4 **HDs 
**80GB WD EIDE** drive 2 partitions (40gb WindowsXP SP2(ntfs)/40gb Ubuntu Feisty Fawn i1386)
**250GB WD SATA** drive: 1 (ntfs)partition  for incoming/to be sorted files and Windows game installs(UT2k4,Q4,WoW,etc.)
**300GB Maxtor SATA** drive: 1(ntfs)partition for various archives and mp3s
**500GB WD SATA** drive 1(ntfs) partition for Anime/pr0n archives

I want to be able to ditch windows for everything but gaming, and eventually even that.
BUT I want all my files to be mountable/writable in both OSes. I've read ntfs = bad for *nix especially for writing. 
Is Fat32 better?   If so, how would I go about converting the partitions to such without losing all my anime?
(If Blu-Ray writers weren't so damned expensive I wouldn't even be having this problem)
If not, is there a method that is stable and reliable for Feisty? 
If so, are there any precautions I need to take in windows, such as file permissions/access privs before mounting?

thanks in advance
DJ

---

### Post by LaRoza on 2007-05-10
You can use Ubuntu to read NTFS, you might have to install ntfs-3g.

FAT32 works but has limitations.

You can not reformat a drive a preserve the information, in this case, you won't need to.

---

### Post by Mutal1ty on 2007-05-10
> **LaRoza said:**
> You can use Ubuntu to read NTFS, you might have to install ntfs-3g.

FAT32 works but has limitations.

You can not reformat a drive a preserve the information, in this case, you won't need to.

I read somewhere that you can "convert a partion to Fat/ntfs, without having to format it, not sure, but I thought I read that somewhere

---

### Post by Mutal1ty on 2007-05-10
> **LaRoza said:**
> You can use Ubuntu to read NTFS, you might have to install ntfs-3g.

FAT32 works but has limitations.

You can not reformat a drive a preserve the information, in this case, you won't need to.

I read somewhere that you can "convert a partion to Fat/ntfs, without having to format it, not sure, but I thought I read that somewhere

---

### Post by Gig103 on 2007-05-10
Mutal1ty,

I still run a dual boot and Ubuntu mounts my NTFS drives for read-only at startup. I haven't had any problems playing MP3s or videos that way, and by installing ntfs-3g, I can even write to them, no problem.

---

