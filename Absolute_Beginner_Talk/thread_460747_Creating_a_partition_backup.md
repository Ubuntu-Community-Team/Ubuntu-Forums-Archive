---
title: "Creating a partition backup"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-06-01
I have a 250gig drive. Currently I have about 90 gigs as the primary for ub, some swap, and the rest unallocated. If I use a program like Partimg, should I be making an extended or a primary partition?

and on the subject, now that I have installed this program via synatpic, how do I get it started? dont seem to see it added in any menus, and partimg in terminal does not work..

---

### Post by AtrejuT on 2007-06-01
you should be able to run it via
```

sudo partimage

```

I'm not sure if I understand the other question correctly: If you want to add new partitions I would create an extended partition and then logical partitions within this extended partitions, otherwise you'll soon hit the limit of no more than 4 primary partitions being allowed.
To create partitions partimage is the wrong program though, try using gparted.

---

### Post by indytim on 2007-06-01
If you are looking at expanding your partitions (ie. add a new one(s)), use GParted Live or other partitioning tools,  and create an extended partition from you unallocated space.  Once the extended partition has been created, then go ahead and add additional partitions as required.  The use of the extended partitions will prevent you from getting into a "partition lock" situation (trying to have more than 4 primary partitions is a no-no).

IndyTim

---

