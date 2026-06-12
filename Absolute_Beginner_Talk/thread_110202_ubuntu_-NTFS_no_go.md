---
title: "ubuntu -NTFS no go?"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by gRiMgRaVy014 on 2005-12-30
I was just reading about installing linux and it said ( from what I got out of it) that ubuntu is better for fat32 drives? Well I right now have a 80 gig NTFS drive. I have a 1.6 gig fat32 but I believe its not big enough am I correct? Someone please explain this to me.

---

### Post by xtacocorex on 2005-12-30
Ubuntu (and Linux in general) can read and write to fat32 partitions, whereas they can only read from ntfs partitions.

The core OS won't run on a fat32 partition so you'll need to resize the NTFS and make and ext2 or ext3 partition for Ubuntu.

I haven't messed with any of the resizing tools (qtparted) so I don't know how well they work, but from what I've heard and read on the forums here, they seem to work pretty well.

---

### Post by Suger on 2005-12-30
Ubuntu can read and write fat32 partitions and only read ntfs partitions. Anyhow, it won't install on either (it has to live on an ext2, ext3 or reiser partition). So you will have to partition your disk to install ubuntu on it.

---

### Post by Rxke on 2005-12-30
1.6 gigs is very probably not big enough, no... 5gigs or more is plenty, if you're not planning to install a big bunch of other stuff afterwards ;)

I have both KDE and Gnome and an assortment of extra stuff on a 9gig partition, and it's still only 1/3 full, 2.8 gigs to be more precice

---

