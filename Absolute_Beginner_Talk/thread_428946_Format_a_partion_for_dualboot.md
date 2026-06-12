---
title: "Format a partion for dualboot?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-04-30
Do i have to format my xp partion to do a dualboot, and if yes what format?

---

### Post by bobplano on 2007-04-30
if you're installing xp and ubuntu for dualboot, you need a couple partitions. install xp first if it isnt installed, then defrag it. put in the ubuntu cd and resize the xp partition with one of the options it gives you. backup your important data just in case. the win xp partition should be ntfs and the ubuntu one should be ext3 but you shouldn't have to worry about that. grub will handle the dualboot but if there is no option for windows you will need to add it, but worry about that later

---

### Post by az on 2007-04-30
In other words, the installer will do all the work for you.  The only decision you need to make is how small to shrink your current windows partition.

---

### Post by mojo123 on 2007-05-01
I just made a  new partion for puppy, for some reason it wont give me the format option

---

### Post by az on 2007-05-02
Are you running the partitioner from a live cd?  You have to unmount all your partitions (including swap space) before you can partition a disk.

---

