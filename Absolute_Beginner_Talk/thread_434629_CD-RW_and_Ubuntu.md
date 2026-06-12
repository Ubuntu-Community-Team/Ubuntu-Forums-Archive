---
title: "CD-RW and Ubuntu"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Campingman on 2007-05-06
I have a couple of CD-RW disks with audio tracks on.  I want to remove these tracks and use the disks for data.
Does Ubuntu support rw disks?
If so how do i access it and manipulate the data.  If I open the disk it will only open in Soundjuicer, "open in a different window" option opens in Soundjuicer also???

---

### Post by - Lazlo - on 2007-05-06
You can install gnomebaker and burn a "blank CD-RW"

You can also do it with the terminal, I thought it was something like this:

cdrecord dev=/dev/**YOUR DEVICE** speed=10 blank=ALL/FAST* padsize=63s -pad -v -eject

* you can choose between blank and fast, blank will give a complete format but takes some extra time

---

### Post by Campingman on 2007-05-06
> **- Lazlo - said:**
> You can install gnomebaker and burn a "blank CD-RW"

You can also do it with the terminal, I thought it was something like this:

cdrecord dev=/dev/**YOUR DEVICE** speed=10 blank=ALL/FAST* padsize=63s -pad -v -eject

* you can choose between blank and fast, blank will give a complete format but takes some extra time

Thanks for that, I will give it a go.  I booted back into XP in the end, it seems this is increasing the less frustrating option for quite a few things!

---

### Post by Efros on 2007-05-06
Haven't tried it as I tend not to use cdrw's but I'm sure K3B will do this.

---

