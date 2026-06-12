---
title: "Does this mean the partition didn't get touched?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by StephanGFX on 2007-07-10
I went to the hp support page for my computer and this is what it said about my built in recovery console:


Where can I get recovery CDs?

HP Media Center computers that ship with Windows XP do not come with recovery CDs. Instead, they use a hidden space (partition) on the hard drive to store the recovery information. Using a hidden partition provides a more convenient, more stable recovery process that eliminates the need for CDs that can be scratched or lost.

So my question is, does that mean that even though ubuntu took over my partition that i had xp on, did the recovory option not get touched? becuase its hidden?

---

### Post by rolfen on 2007-07-10
I'd advise to run Gparted and try to see if this partition is still present,

---

### Post by StephanGFX on 2007-07-10
is gparted on the bootcd for ubuntu?

---

### Post by regomodo on 2007-07-10
why have you started a new thread about the same thing? 

You have wiped the whole drive. If xp isn't there anymore you have told the Ubuntu installer to use the **entire **drive

---

### Post by pistcivet on 2007-07-10
It wouldn't hurt to look at your partitions.
Recovery partition might be there.
Try this:
```
sudo parted
print
quit
```

---

