---
title: "[Win7] &quot;CHKDSK is resetting Usn information... &quot;"
date: 2012-11-09
forum: Any Other OS
---

### Post by nikonian on 2012-11-09
Hi guys.

I have a BADLY corrupt hard disk (1Tb WD Caviar Green) which has been RMA'd and a replacement on its' way... but in the meantime, ALL my data was almost gone forever. I have used:

1/ TestDisk

2/ Fixparts

and a few other tools. It seems good old chkdsk has rebuilt most of the NTFS partition upon which resides my VITAL data which remains - the stuff I need. The next day, the data partition I want to access stopped mounting, with Nautilus complaining about "no such..." something or t'other, and something about MFT and MFT mirror missing (bad?).

Chkdsk has given me various messages about having recovered/re-indexed missing files, having made various corrections etc (this drive has a LOT of bad sectors, but I've recovered 2/3rds of what I needed so far?). My chkdsk session for the vital data partition is @ 30% after almost 4 hours, and currently says:

"CHKDSK is resetting Usn information..."

This message came AFTER it re-indexed (or whatever) the "Missing" files - do I NEED this USN journal resetting, or, now that the re-indexing seems to have completed, may I just stop the process and try to get my data off the drive? This seems like it is going to take HOURS and HOURS more :/

The drive's toast anyway, and I'm gonna zero and bin it afterwards, once the replacement comes, so it's of no value to me... but is this journal VITAL? Can data be recovered WITHOUT it (IE: Does the MFT still exist without it?). I'm not disk savvy to the Nth degree like some :p

Thank you :)

---

### Post by oldos2er on 2012-11-09
Moved to Other OS/Distro Talk.

---

### Post by nikonian on 2012-11-09
> **oldos2er said:**
> Moved to Other OS/Distro Talk.

Bah! Thought that was an answer :p hehe

---

