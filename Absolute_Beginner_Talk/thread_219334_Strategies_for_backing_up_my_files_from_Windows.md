---
title: "Strategies for backing up my files from Windows"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by mwshook on 2006-07-19
My MBR under WinXP got corrupted, and I decided that would be a good reason to go back to Linux. Windows won't boot, but I still have the ability to access my hard drives under the Ubuntu live CD.

I have over 8 years worth of stuff on that drive. I've got all the small important stuff like Word documents backed up, but I'd rather not lose my MP3's and video files if I don't have to (approx 50 gigs worth of stuff). I'd like to have everything backed up before I have the Ubuntu intall start messing with partitions and repairing the MBR. My original strategy was to put everything on a stack of DVD+R's, but that hit a roadblock.

When I use the "CD/DVD Creator" I get an error about invalid filenames. I'm used to getting a similar error when I made CD's in Nero (file-names being too long), but Nero gave me an option to automatically truncate the filenames. The ubuntu program doesn't give me that option and won't even tell me the names of the offending files.

My other option would be to move my most important 37 gigs worth of stuff to my secondary drive. I tried to do this (I have to run Nautilus under sudo to even read the NTFS drives) but it says they are read only, even in a root terminal.

Any suggestions about how to move this data to DVDs or the other drive?

---

### Post by Kurt` on 2006-07-19
> **mwshook said:**
> My other option would be to move my most important 37 gigs worth of stuff to my secondary drive. I tried to do this (I have to run Nautilus under sudo to even read the NTFS drives) but it says they are read only, even in a root terminal.
When you "move" a file, it makes a copy, then deletes the original.

Deleting requires write access, and your NTFS partition/drive is mounted read-only (as linux doesn't support NTFS writing perfectly yet). That's why you're getting an error when trying to move.

---

### Post by Drakkor on 2006-07-19
I don't know,I can copy things from my windows ntfs partitions,and paste them in ubuntu.

---

### Post by mwshook on 2006-07-19
I'm trying to copy from one NTFS drive (C:) to a second NTFS drive (D:) so I can go ahead and format C.

If ubuntu doesn't support writing to an NTFS drive, is there another distro's live CD I could use for that?

---

### Post by Kurt` on 2006-07-20
As I mentioned before, Linux can't write to NTFS perfectly yet, although there have been huge breakthroughs recently (google for "ntfs-3g").

Why can't you just copy (instead of "move") everything over, then format the NTFS partition?

---

