---
title: "Installing ubuntu for the first time"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by dpar on 2006-10-24
Hi. I am trying to install ubuntu on my computer which already has windows on an 80gb drive. I also have a 120gb drive that has 4 partitions roughly 30gb each.
 I would like to install ubuntu on one of the 30gb partitions, but the installer doesn't recognize the individual partitions, it thinks of it as one big drive that is partially used.
 Is there any way to do this so that windows still sees the 4 individual partitions?

---

### Post by bulldog on 2006-10-24
Did you make an empty partition?

If so remove the empty partition so you get unallocated space.

Don't format it in anyway and let Ubuntu use this space to install itself.

---

### Post by Aberrix on 2006-10-24
do a 'manually edit the partition tables'

then mount "/" to the partition you want.

---

### Post by dpar on 2006-10-24
Thanks for the info guys. I finally had to take everything of the second drive to get it installed.I guess it wasn't 'partitioned' in the first place, just virtual drives.
Anyway, one more question......how can i get ubuntu to see or mount the windows drive? I would like to be able to access those files as well.
Anyway, thanks again, I'm off to see if i can change around the boot order in grub.

Dave

---

