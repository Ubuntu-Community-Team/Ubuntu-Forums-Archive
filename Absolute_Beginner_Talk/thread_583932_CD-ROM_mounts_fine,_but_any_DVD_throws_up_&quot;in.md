---
title: "CD-ROM mounts fine, but any DVD throws up &quot;invalid mount option&quot;"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by JoeTheZombie on 2007-10-20
Hi.  I place a CDROM in the drive and Gutsy has no problems mounting it.  However, I put any DVD disc in the drive, and I get an error:  "Invalid mount option when attempting to mount the volume."

---

### Post by Pumalite on 2007-10-20
Check /dev and see which and how many devices you have.

---

### Post by wizkey on 2007-10-21
I'm encountering a similar problem.

Upgraded from 7.04 to 7.10. Drive is a combo DVD-ROM/CD drive that worked just fine under 7.04. Now under Gutsy it throws this error. Checked fstab, it's the same as it was before the upgrade.

Interestingly, it only throws an error if I put a CD in the drive. Put in a DVD, it has no problem.

Here's the line from fstab, it should have no problems mounting a CD.

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Just a guess, but Gutsy just doesn't seem to recognizing the iso9660 type when a CD gets put in. I'm guessing it's trying to mount the CD with UDF, and so throwing the error.

Going to modify fstab and remove UDF and leave iso9660 and see what it does.

Edit: Yep, as I suspected, removing UDF allowed the CD to be mounted. Curiously, with UDF removed it was still able to mount a DVD. I would have thought it would fail without UDF being specified.

---

