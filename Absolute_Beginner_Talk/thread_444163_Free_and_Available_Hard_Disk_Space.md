---
title: "Free and Available Hard Disk Space"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by yanewby on 2007-05-15
One of my hard drives is becoming too full and I have been looking at the statistics given in System -> Administration -> System Monitor on the File Systems tab.

I notice two of the columns are - Free and Available disk space.  The free column seems to be in general about 10Gb larger than the available column.

What causes this difference?  Is there any way to make any more of the "free" space "available"?

---

### Post by indytim on 2007-05-15
Do you have "unallocated" free space on your harddrive?  Sounds like you do.  Get ahold of a partition editor (GParted) is my favorite and check things out.  The editor will also allow you to resize partitions.  Before going this route do a search on these forums for partition resizing etc.

IndyTim

---

### Post by yanewby on 2007-05-15
I used GPartEd to format the hard drives in the first place and there appears to be no unallocated disk space when I double-check with it.

Any other ideas?  I would like to know what the difference between "free" and "available" is.

---

### Post by jhenager on 2007-05-15
I wonder if the difference can be accounted for by checking the trash. If something is in there, it might be counting against the total for available space.

---

### Post by laidback on 2007-05-15
Could it be that your wastebin has lots of deleted files in it. You'll need to empty it to release the space. If you're using Gnome bottom right of screen, click wastebin then delete as required. Not certain that this is the answer but it's worth a check.

Mine has a difference of around 0.5Gb with an empty home wastebin.

---

### Post by stalkingwolf on 2007-05-15
Think in terms of your checking account.   Available balance and posted balance.  Your free space/posted balance is how much resource you have.  The available balance/space is what you have after pending
transactions/operations or that which is set aside for a reserve/cache or OS use.  Many times this cache
can be modified/ reduced to free up usable space.

---

### Post by yanewby on 2007-05-15
The Trash bin being full was my first thought but even after emptying it there is still a difference of 10Gb+.

I liked Stalkingwolf's analogy and I think I understood that.  How would I go about freeing up the available space?

---

