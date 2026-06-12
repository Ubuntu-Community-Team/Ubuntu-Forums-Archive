---
title: "Gparted | Can't resize partition [pic]"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-15
Hey!

I've decided I want to create a seperate partition for all my media and stuff. 

The problem is, after downloading and installing gparted, I can't modify anything.

A screenshot is attached. Can someone help?

I have all priviledges.

---

### Post by Nikron on 2007-06-15
You can't partiton a mounted partition.  See where it says "unmount", well you have to do that.  And you can't really do that on a system running off the hdd.  So, really you have to grab the gparted iso and use that.

---

### Post by yabbadabbadont on 2007-06-15
All your partitions are in use because you are booted using them.  You will have to boot using a live cd that includes gparted in order to resize them.

Edit: Yet again, I'm too slow.  :D

---

### Post by overdrank on 2007-06-15
> **yabbadabbadont said:**
> All your partitions are in use because you are booted using them.  You will have to boot using a live cd that includes gparted in order to resize them.

Edit: Yet again, I'm too slow.  :D

A+ for the effort!;)

---

### Post by alecwh on 2007-06-15
Is it risky to resize?

I have a live cd, how do I resize without reinstalling the OS?

---

### Post by ryanVickers on 2007-06-15
You could just boot from the ubuntu live cd and use the gparted trhere.  It sais to back stuff up first, but I've never had a problem with it, and I've done some insane stuff!

---

