---
title: "Resizing partitions"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by qwazert on 2007-01-07
Does anybody know how I could accomplish the following...

I have a 30Gb harddrive. 20 Gb have been devoted to Windoze, and the remainder to Ubuntu and its swap partition (600Mb).
I wanted to increase the LINUX partition, so I started by shrinking the Windoze partition first. That went off without a hitch...however Gparted would not allow my LINUX partition to be resized. Furthermore, the only thing I could do with the space left over from resizing Windoze, was to reformat it into YET ANOTHER partition...it wouldn't allow me to simply blend it into the LINUX partition.
Did I do something wrong, or is what I am trying to do simply NOT possible with the disk structure the way I have it now?

---

### Post by jvc26 on 2007-01-07
Are you doing this from Gparted on the live cd or on the Gparted cd? As it may sound stupid, but you obviously cannot do it from Gparted installed within your Ubuntu partition (as you can't resize a partition which is mounted) - Im not suggesting you are stupid, its not too hard to make an oversight :)
Il

---

### Post by qwazert on 2007-01-07
I am running Gparted from the CD.

I can resize the largest partition but I cannot meld the freed space into the next partition. I have a feeling I may need to delete the LINUX partition altogether and make a new one from the newly freed space AND the old LINUX partition.

I wish I didn't have to do that!

---

### Post by fredster001 on 2007-01-07
i had a similar problem.

You need to run Gparted from the Gparted CD, and then you get lots more functions.

---

