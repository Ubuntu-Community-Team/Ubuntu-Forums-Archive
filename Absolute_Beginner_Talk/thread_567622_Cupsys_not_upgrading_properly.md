---
title: "Cupsys not upgrading properly"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by ace214 on 2007-10-04
I have upgraded to Gutsy in the past few days and am now getting this message trying to upgrade cupsys:
> E: /var/cache/apt/archives/cupsys_1.3.2-1ubuntu4_i386.deb: trying to overwrite `/usr/share/doc/libcupsys2/CREDITS.txt', which is also in package libcupsys2

Is there anything I can do about this?

---

### Post by Paulmd on 2007-10-04
> **ace214 said:**
> I have upgraded to Gutsy in the past few days and am now getting this message trying to upgrade cupsys:


Is there anything I can do about this?

Delete the credits.txt file and try the upgrade again. Not to worry, all that's in that file is names of the developers, and so forth.

---

### Post by nike984 on 2007-10-04
> **ace214 said:**
> I have upgraded to Gutsy in the past few days and am now getting this message trying to upgrade cupsys:


Is there anything I can do about this?

Same thing happened for me.
I'll try to remove the credit file later and post the result.
Thanks anyway

---

### Post by xyverz on 2007-10-04
I did remove the file.  I still got the error.  Just did another update and trying another upgrade.  Seems more packages are being upgraded this time.  Will post my results here.

---

### Post by RomeReactor on 2007-10-04
Hi. Try the solution [posted here]("http://ubuntuforums.org/showpost.php?p=3475508&postcount=4") (after the bug report).

Problem related to Gutsy should be posted in the [Development (Gutsy Gibbon)]("http://ubuntuforums.org/forumdisplay.php?f=238") section.

---

### Post by xyverz on 2007-10-04
Thanks Rome, the --force-overwrite worked perfectly.  :-D

---

