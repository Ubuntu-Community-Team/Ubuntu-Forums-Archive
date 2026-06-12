---
title: "Need Help REALLY Badly: GParted Problems"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by DizzyTech on 2006-11-24
Um, hi, I had resized my NTFS partition smaller to install Ubuntu.  After having problems with the install, I had gotten rid of the partitions added on after the NTFS partition.  I then used GParted to expand the NTFS partition back to the whole drive.  Well, here's the problem.  GParted halted with a "NTFS Journal unclean" error.  So, GParted comes up as the NTFS being the whole drive, with the first 20 GB (the size of the resized partition) being full.  In Windows, my NTFS hard drive is the same 20 GB.  In the Computer Manager, it also shows the whole drive being taken up by a healthy NTFS, yet the partition stills shows as 20 GB.

I really need this to be fixed so I don't magically lose 17 GB off my hard drive.  Please help.
:confused:

---

### Post by Kevin on 2006-11-24
Not quite sure, but you could try running chkdsk (or chkdisk, can't remember) in windows command prompt.  After that try re-resizing it to something, then expanding it again.

---

