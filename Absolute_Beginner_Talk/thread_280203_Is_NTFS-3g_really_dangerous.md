---
title: "Is NTFS-3g really dangerous?"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by uzd4ce on 2006-10-19
I just set up NTFS-3g to access (read & write) the Windows drives on my machine.  I've seen various references to NTFS writing being potentially dangerous with the possibility of data corruption.

Is that still the case with NTFS-3g?  And if I am risking data loss, are we talkign about what I'm trying to write at the time, or is there potential risk to the entire drive?

The particular drive I'm accessing is just a data drive.  Am I better off copying everything off, and reformatting it as FAT32?

Thanks

---

### Post by Magnes on 2006-10-19
I lost some files (folders) using NTFS-3g in the first version. Don't know how risky is the newest one.

---

### Post by randiroo76073 on 2006-10-19
AFAIK ntfs-3g is not stable yet, it still has the possiblity for data corruption, the best bet is to backup your data first, if it were me I'd convert to fat32 then reload data :)

---

### Post by delphiguy on 2006-10-19
I have been using ntfs-3g for about 3 weeks now and Im glad to say that I am very much satisfied with it.  Although I have to say that sometimes when transferring a big file or folder, it gives me an error I cant remember the error anymore but it has something to do a folder was not found or something to that effect.  But this only happens when I was transferring file/folders from one ntfs partition to another, but since I formatted my other ntfs partition into ext3, and leaving just 1 ntfs partition I no longer had that problem.

Overall its a great tool especially for people like me who is trying to put windows out of my life.

---

### Post by Kurt` on 2006-10-19
Used it to repair a relative's rootkitted XP installation (replaced a few files, svchost.exe, explorer.exe, etc.) a few weeks ago... perfectly fine. :)

As for using it 24/7, no clue.

---

### Post by PriceChild on 2006-10-19
MS have not released the specs for the ntfs filesystem.

Therefore all use of linux on ntfs is guesswork/trial & error.

If you use it, backup all data and be prepared for data loss.

Pricey

---

### Post by aknapp on 2006-10-19
Here is what I'm wanting to do:

Setup a universal folder for azureus in either winxp or ubuntu to download to. For instance no matter what OS im currently in, azureus will be downloading to the same location (ie on my xp part). 

So in order to do this I would either need read/write support in linux (as xp cannot access linux in a true sense), a fat32 partition, or to convert xp from ntfs to fat32 all together. Right? Is using ntfs-3g in this way a good idea?

---

### Post by orb9220 on 2006-10-19
Because of the nature of hashing for downloading files from torrents,etc...
I would not feel comfortable with 3g.

I have a fat32 setup for this kinda thing where all my downloads,pics,music,etc.. are stored and accessed by ubuntu and xp.

---

### Post by aknapp on 2006-10-19
Thanks, thats what I wanted to know.

*ps. your avatar gives me nightmares*

---

