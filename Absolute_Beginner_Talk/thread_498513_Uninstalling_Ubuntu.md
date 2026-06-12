---
title: "Uninstalling Ubuntu"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by StephanGFX on 2007-07-11
Ok, when I was trying to dual boot ubuntu and windows xp, I messed up and ubuntu took over my whole partition and erased my recovery console. I was able to get my hands on some recovery cds from my friend, who has the same computer as I do. What I need to know is, what do I do to make sure it completely deletes ubuntu and grub, and what I need to do before I start the recovery process. Thanx

---

### Post by LaRoza on 2007-07-11
When you recover, it will bring the drive back to where it was when you bought it, nothing needs to be done.

If you wanted to manipulate partitions, using GParted is the best solution, (in my sig).

---

### Post by 505 on 2007-07-11
To delete ubuntu just delete the partition ubuntu is on. You can then use partitioning software the add this space to you windows partition again (no idea if you can get the recovery files on there back again).

To uninstall grub and use the windows boot loader, boot the windows recovery console and the 'fixmbr'

---

### Post by gn2 on 2007-07-11
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by rickycodie on 2007-07-11
most windows recovery cds will have the option to erase a hd and install window$.

then on the reinstall of buntu use gparted to resize your windows, then click use greatest free space to install and you'll be fine.

---

