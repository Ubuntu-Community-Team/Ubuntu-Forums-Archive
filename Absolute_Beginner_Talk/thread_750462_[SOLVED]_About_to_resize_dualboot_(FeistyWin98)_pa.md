---
title: "[SOLVED] About to resize dualboot (Feisty/Win98) partitions. Advice requested."
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by swarup on 2008-04-09
I've got a 10 GB HD on my laptop, with ~6 GB for Feisty and ~4 GB for Win98. There is 1.4 GB free on the Win98 partition, and I want to upsize the Feisty partition by 1 GB. First I defragged the Win98 partition, and backed up all my data from both partitions. I have the Parted Magic 2.1 live cd, and just booted up to it to see how the scene looks. The Win98 partition is on the left side, and the Feisty partition on the right. Feisty currently has about 500 MB free on it. My question is this: By downsizing the Win98 partition by 1 GB, that newly freed up space will be to the left of the Feisty partition. While the 500 MB of free space in Feisty is on its right side. So when I expand Feisty's partition to the left to take on the free 1 GB, I am imagining that there will be 1 new free GB on the left side in the Feisty partition, and the free 500 MB on the right side in the partition. With the OS and data etc sandwiched in between. Is that alright? Or should all the free space in the partition be together? And if so, then how would I move the Feisty OS and data to the left end of the partition so all the free space (1 GB + 500 MB) will end up together on the right?

---

### Post by Shazaam on 2008-04-09
Usually, when you resize/move a partition to the left the files will be automatically moved to the start (left side) of the partition. That way the free space ends up on the right side. You would end up with this......

Partition 1= Win98 and .4gig free space./Partition 2= Ubuntu and 1.5gig free space.

Do you have a swap partition set up for Ubuntu? 500mg would be fine.

---

### Post by Average Joe on 2008-04-09
The stuff you see in Parted Magic is probably just a graphical interpretation. When you resize, you´ll probably find your extra space of Feisty on the very right.

---

### Post by swarup on 2008-04-09
That is just what I wanted to hear.  :) Thanks to both Shazaam and Average Joe for your reassurance. I'll go ahead with the resize now. Assuming all goes smoothly, I'll come back here and mark this post as [SOLVED].

Add: Yes, I do have a Swap partition. The one which Ubuntu originally created when I set up the dual boot almost a year ago. I assume nothing will need to be changed with that.

---

