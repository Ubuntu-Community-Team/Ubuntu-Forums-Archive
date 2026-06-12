---
title: "Resizing a partition without repartitioning?"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-07-19
I need to enlarge my swap partition, and I was wondering if I could just take some extra space from my home partition and add it to the swap partition, without losing any of my files on my home partition.  Is this possible?

Thanks.

---

### Post by tuxcantfly on 2007-07-19
boot up the Ubuntu Desktop CD, start up GParted (System -> Administration -> Partition Editor) and that'll let you shrink and resize your partitions

---

### Post by mikewhatever on 2007-07-19
Yes, if they are adjacent. You can use the Partition Editor on the live CD in System>Admin, or gparted Live CD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Yes on 2007-07-19
By adjacent, you mean when you do that command in the terminal (What is it?  The one that lists all the partitions and their sizes?), they will be listed with home on top of the swap partition in the list (Or vice-versa).

Or will the partitions have numbers, and so if the home partition is number two, and the swap is number three, they're adjacent?

Sorry, I haven't used Ubuntu in a while.

Thanks.

---

### Post by Yes on 2007-07-19
Bump.

---

### Post by tuxcantfly on 2007-07-20
> By adjacent, you mean when you do that command in the terminal (What is it? The one that lists all the partitions and their sizes?), they will be listed with home on top of the swap partition in the list (Or vice-versa).


Well you shouldn't really be concerned about that, you just want to change your swap size; you can just delete your swap partition, shrink the home, and recreate the swap next to the home partition if they aren't already next to each other; there's no data on the swap partition  (other than temporary files and the like) anyhow so you can basically do whatever you want, just resize, don't delete, your home partition when using GParted. Answering your question, though, that was referring to how the partitions are shown shown in GParted's GUI.

---

### Post by mikewhatever on 2007-07-20
> **Yes said:**
> By adjacent, you mean when you do that command in the terminal (What is it?  The one that lists all the partitions and their sizes?), they will be listed with home on top of the swap partition in the list (Or vice-versa).

Or will the partitions have numbers, and so if the home partition is number two, and the swap is number three, they're adjacent?

Sorry, I haven't used Ubuntu in a while.

Thanks.

Adjacent only means they are next to each other with no other partitions in between. This way, you can shrink one and expand the other.

---

