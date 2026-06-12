---
title: "help with gparted and partitioning a harddrive!!"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by totallylost on 2006-03-11
i just used gparted to create a 41gb unallocated space (for kubuntu--not installed yet) and 145gb of space for windows xp (already installed).

im wondering if i need to do anything to the unallocated space? Can i just leave it as is and go to install kubuntu or are there other steps i need to take?

Also when i do go to install kubuntu i need to know what sort of partitioning ill need to do to that 41gb space i have for kubuntu.  do i need to have a swap file? or can i just tell it to install itself on the 41gb partition and let it go at that- will i need to make other partitions within that 41gb partition to have kubuntu run correctly?

sorry about my stupidity-im still a noob

---

### Post by mlind on 2006-03-11
here's what I usually do

first, I create chunk of unallocated space, just like you did. Then I let distribution's
own wizard to suggest how it would allocate the chunk. 

Normally I end up with this setup:

swap partition, size of my RAM
/ (root) partition, from 5-8 gigabytes. Marked as bootable, so /boot mountpoint is created here too.
/home partition, rest of the space

separate /home partition is good, because you can share this with other linux
distributions or when you have to upgrade. This ensures that all user specific
content will persist even if you need to completely wipe out ubuntu.

After I've installed Ubuntu (desktop), and few extras. / (root) is only 35% full, so
there's plenty of room for extra packages.

---

### Post by syg00 on 2006-03-11
I *think* it'll do everything for you - swap included.
I preallcoate everything, so I just had to sort out the mount-points.

Just do it, and tell it to use the unallocated space. It may not make the best choice, but it'll certainly be usable.

---

