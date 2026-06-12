---
title: "[SOLVED] Partitons need to just make 100% sure."
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by travismoore on 2008-02-07
OK i have an 80GB and an 500GB

I was going though set-up for Ubuntu but have come out and into windows to make 100% that i setting this up right.

**80GB: **
40GB Windows (set as /windows) (NTFS)
38GB Ubuntu (set as /  ) I presume thats root (EXT3)
2GB swap (set as swap) 

**500GB:**
460GB Im using for file storage but im not sure do i set it as /windows ?  (NTFS)
40GB set as /home (this i think is correct) (EXT3)

I have it set up like this so i can update Ubuntu without affecting settings and re-install windows when its getting sluggish.

Are all these partitions and stuff right?

---

### Post by pieisgood4589 on 2008-02-07
Yup, they're perfect! I have low RAM, though (192mb) so I allocated 2.5gigs to swap. :lolflag:

---

### Post by forrestcupp on 2008-02-07
That looks like it would work.  Just make darn sure not to format your main Windows partition, and don't format the 460 GB windows one if it already has files on it.

---

### Post by travismoore on 2008-02-07
Yea I'm going to be very careful with that don't want to loose my music collection. With the two EXT3 partitons and the swap do i need to tick the format box next to them if i already partitioned it all out (system>admin>partition editor) before i started the install?

---

### Post by Rocket2DMn on 2008-02-07
Hello again.
80GB looks pretty good (though you won't truly have 80 full GB to deal with, more like 75 probably).  Probably want to mount the windows partition at /media/windows
500GB (not truly 500, probably like 485GB): your ~460GB data partition you could mount at something like /media/data  or /media/storage
Otherwise looks good.  Don't forget to defrag!

---

### Post by Tyke91 on 2008-02-07
no need to, but it wouldn't hurt you 

just make sure you label everything right, one root (/), /home and swap. (you don't really need a home partition, but it makes things really easy later on)

---

### Post by travismoore on 2008-02-07
> **Rocket2DMn said:**
> Hello again.
80GB looks pretty good (though you won't truly have 80 full GB to deal with, more like 75 probably).  Probably want to mount the windows partition at /media/windows
500GB (not truly 500, probably like 485GB): your ~460GB data partition you could mount at something like /media/data  or /media/storage
Otherwise looks good.  Don't forget to defrag!

Yep i know its not actually 80GB (because of hdd being measured in 1000MB rather than 1024MB for some strange reason). 

Yep i de-fragged 3 times lol =D

hopefully next post will be from ubuntu (probably with some more problems lol)

Cheers,

Travis

---

### Post by forrestcupp on 2008-02-07
Format the root partition, and the /home partition too, unless you have previous settings and files you want to keep.  If it gives you the option to format swap, go ahead and do it.  If it's been formatted as a swap before, you never need to do it again, but the first time it probably does need formatted.

---

