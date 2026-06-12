---
title: "LVM and EVMS --- what for?"
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by roots on 2005-07-08
hi there...

i'm just trying to speed up the ubuntu boot process so i stumbled over LVM and EVMS... what are these services good for and - do i actually need them if i don't use a raid system?

cheeers,
.roots

---

### Post by skirkpatrick on 2005-07-08
It's not just a matter or RAID.  You can have a RAID system without them.  What they do allow you to do is add another harddrive later on and have the system think you have just one, bigger harddrive instead of having to migrate everything from the old drive to the new one.  You can put two 80GB drives in your system and Ubuntu will think you have a single 160GB one.  It's easier to do it from the very beginning instead of deciding to do it later.

---

### Post by roots on 2005-07-08
ok thx! so if i do get you right, there's not much use for LVM and EVMS if i'm using a single 80 gig hdd in my notebook?!

.roots

---

