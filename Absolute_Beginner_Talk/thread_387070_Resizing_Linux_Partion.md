---
title: "Resizing Linux Partion"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by atraeyu on 2007-03-17
I installed Ubuntu on my laptop which has a 60gb hd.  I left xp on a 40gb partition and installed ubuntu on a 19gb /ext3 partition.  I just cleared everything except the barebones out of xp and shrunk the partition down to 25gb.  I'd like to add the extra 15gb to the /ext3 partition.  

I'm not quite sure how to go about this.  Anyone have any suggestions?

---

### Post by Bachstelze on 2007-03-17
Save all valuable data and use the GParted Live CD to move your partition. Be warned, it will take a while.

---

### Post by soul814 on 2007-03-17
Pretty sure I remember that you can't resize a ext3 partition. You have to save all your data and reformat and install. Technically linux doesn't take up that much space. Make a fat32 partition for storage. Both windows and linux can access it.

---

### Post by Bachstelze on 2007-03-17
Yes you can, I did it just yesterday...

---

### Post by az on 2007-03-17
Since the windows partition (I am guessing) was before the ubuntu partition and the space you cleared up is smaller than the partition you want to shuffle around, you cannot do it.

You would be able to add the free space to the end of the partition, but not the beginning.  If the free space was a little larger, you would be able to move (copy) the linux partition there, delete the old linux partition and extend the new linux partition with the free space at the end.  

Since moving the current linux partition to the free space would involve writing over the first 4 gigs of the partition you want to copy, the partitonner will not do it.

You could always just create an ext3 partition there and use it as storage and mount it as a folder in your home drive.

---

