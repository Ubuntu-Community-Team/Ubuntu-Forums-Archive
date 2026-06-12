---
title: "Partioning /, /boot and /home?"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by melbo on 2007-12-29
OK...  I have searched and searched and still haven't found it.

I've played with my Gutsy install for a couple weeks now and have messed up a few things.  Am going to fresh install again.  I've read about setting up a partition for /home as well as /boot.

I currently have followed the ubuntu install instructions to make a /(root) and a swap.

If I use gparted on the live CD, and create all these partitions: /, /boot, /home and swap, How do I then tell ubuntu where these directories are after the install?  I'm trying to free myself up for a future upgrade to Hardy without having to do the Documents backup and reinstall.

I've looked around at trying to "re-direct" my "Pictures" Dir and can't seem to get it.  I'm a former Xp user and it was an easy right click and browse function to do this.  I know I'm missing it but need a pointer.

Also, if I set up /boot, does ubuntu use it automatically on install or do i need to move my boot folder over there as well?  I'm ditching my dual boot system and kicking XP out the door.

Thanks

---

### Post by mikewhatever on 2007-12-29
You'd have to mount all of them appropriately not after, but during the installation, at the partitioning stage. A mount point will tell Ubuntu what each of the partitions is. I don't quite see a point for a boot partition, since you'll only have Ubuntu installed.

---

### Post by melbo on 2007-12-29
Thanks.  I'll skip the /boot.  I suppose that was a safer place to store dual boot info huh?
I'll give it a try.

---

