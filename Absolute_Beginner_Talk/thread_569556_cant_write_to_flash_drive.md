---
title: "cant write to flash drive"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2007-10-07
hey i cant write to it, i can read it, but even as root i cant write to my flash drive, it mounts as /media/MY DATA
i really really need to write to this drive because my assignment is due tomorrow, im pretty desperate

the flash drive is NTFS btw if that helps, but like i said even as root i cant write files to it or drag and drop to it, it keeps saying that its read only :S help!

---

### Post by PmDematagoda on 2007-10-07
Have you installed ntfs-3? Without it you cannot write to NTFS file systems at all.

---

### Post by dynamethod on 2007-10-07
yes ive installed that and choose to write to NTFS, still says that the drive is read only

---

### Post by startherepodcast on 2007-10-07
Hi,
I would advise you to just format it FAT32 with gparted (sudo apt-get gparted in the terminal, then in system -> Administration -> Gpated, the rest should be self explanatory), but you can also enable ubuntu to write to NTFS (the more complicated method), a quick search on the forums should do the Trick

Hope that helped

Leon

---

