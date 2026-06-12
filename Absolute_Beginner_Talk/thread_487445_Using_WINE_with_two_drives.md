---
title: "Using WINE with two drives?"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-06-29
I have Win XP on one HDD and Ubuntu on a separate HDD. Can I use WINE (installed on my Ubuntu HDD) to run WordPerfect from my Win XP HDD? Or, do I need to Install Win XP on the same HDD in a separate partition?
Thanks for your input.

---

### Post by speaker219 on 2007-06-29
Might not be a good idea, people report it crashes alot:
[http://appdb.winehq.org/appview.php?iAppId=530](http://appdb.winehq.org/appview.php?iAppId=530)
If you wanted to use wine on an external drive, cd to /media/[the drive windows is installed on]
for me, its /media/sda2
if you don't know where it's installed,  run:
cd /media
dir
then pick one that's not a cd drive and see if thats your windows drive.
hope that helps.

---

### Post by speaker219 on 2007-06-29
Also, it seems to be possible to run WordPerfect natively without Wine:
[http://linuxmafia.com/wpfaq/](http://linuxmafia.com/wpfaq/)

---

### Post by kittyhawk63 on 2007-06-29
> **speaker219 said:**
> Also, it seems to be possible to run WordPerfect natively without Wine:
[http://linuxmafia.com/wpfaq/](http://linuxmafia.com/wpfaq/)

Thanks for your replies.
kh

---

